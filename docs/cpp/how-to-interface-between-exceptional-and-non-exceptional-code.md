---
description: '자세한 정보: 방법: 예외 코드와 비 예외 코드 간 인터페이스'
title: '방법: 예외 코드와 비 예외 코드 간 인터페이스'
ms.custom: how-to
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
ms.openlocfilehash: 34a0966d496e5e22099de051a74f3458d1cc05d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114028"
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>방법: 예외 코드와 비 예외 코드 간 인터페이스

이 문서에서는 C++ 모듈에서 일관된 예외 처리를 구현하는 방법 및 예외 경계에서 이러한 예외를 오류 코드에서 및 오류 코드로 변환하는 방법을 설명합니다.

경우에 따라 C++ 모듈은 예외를 사용하지 않는 코드(비예외 코드)와 인터페이스로 연결해야 합니다. 이러한 인터페이스를 *예외 경계* 라고 합니다. 예를 들어 C++ 프로그램에서 `CreateFile` Wind32 함수를 호출할 수 있습니다. `CreateFile`은 예외를 throw하지 않습니다. 대신 `GetLastError` 함수로 검색할 수 있는 오류 코드를 설정합니다. C++ 프로그램이 특수한 경우라면 일관된 예외 기반의 오류 처리 정책을 지키는 것이 좋습니다. 비예외 코드와 인터페이스로 연결하므로 예외의 중단을 원하지 않을 것이며 C++ 모듈에서 예외 및 비예외 기반 오류 정책의 혼합을 원하지도 않을 것입니다.

## <a name="calling-non-exceptional-functions-from-c"></a>C + +에서 비 예외 함수 호출

C++에서 비예외 함수를 호출하는 경우 오류를 검색한 다음 예외를 throw할 수 있는 C++ 함수에서 해당 함수를 래핑합니다. 이러한 래퍼 함수를 디자인하는 경우 먼저 제공을 위해 throw 없음, 강력 또는 기본 같이 예외 보장의 형식을 결정합니다. 두 번째로 예외가 throw된 경우 모든 리소스(예: 파일 핸들)가 올바르게 해제되도록 함수를 디자인합니다. 일반적으로 이는 스마트 포인터 또는 유사한 리소스 관리자를 사용하여 리소스를 소유함을 의미합니다. 디자인 고려 사항에 대 한 자세한 내용은 [방법: 예외 보안 디자인](how-to-design-for-exception-safety.md)을 참조 하세요.

### <a name="example"></a>예제

다음 예제에서는 Win32 `CreateFile` 및 `ReadFile` 함수를 사용하여 내부적으로 두 파일을 읽고 여는 C++ 함수를 보여 줍니다.  `File` 클래스는 파일 핸들에 대한 RAII(Resource Acquisition Is Initialization) 래퍼입니다. 해당 생성자는 "파일을 찾을 수 없음" 상태를 감지하고 C++ 모듈(이 예제에서 `main()` 함수)의 호출 스택 위로 오류를 전파하기 위해 예외를 throw합니다. `File` 개체가 완전히 생성된 후 예외가 throw된 경우 소멸자는 파일 핸들을 해제하기 위해 자동으로 `CloseHandle`을 호출합니다. (원하는 경우 ATL (액티브 템플릿 라이브러리) `CHandle` 클래스를 동일한 용도로 사용 하거나 `unique_ptr` 사용자 지정 deleter와 함께 사용할 수 있습니다.) Win32 및 CRT Api를 호출 하는 함수는 오류를 검색 한 다음 로컬로 정의 된 함수를 사용 하 여 c + + 예외를 throw 합니다 `ThrowLastErrorIf` .이 함수는 `Win32Exception` 클래스에서 파생 된 클래스를 사용 합니다 `runtime_error` . 이 예제의 모든 함수는 강력한 예외 보장을 제공합니다. 언제든지 이러한 함수에서 예외가 throw되면 리소스가 손실되지 않고 프로그램 상태가 수정되지 않습니다.

```cpp
// compile with: /EHsc
#include <Windows.h>
#include <stdlib.h>
#include <vector>
#include <iostream>
#include <string>
#include <limits>
#include <stdexcept>

using namespace std;

string FormatErrorMessage(DWORD error, const string& msg)
{
    static const int BUFFERLENGTH = 1024;
    vector<char> buf(BUFFERLENGTH);
    FormatMessageA(FORMAT_MESSAGE_FROM_SYSTEM, 0, error, 0, buf.data(),
        BUFFERLENGTH - 1, 0);
    return string(buf.data()) + "   ("  + msg  + ")";
}

class Win32Exception : public runtime_error
{
private:
    DWORD m_error;
public:
    Win32Exception(DWORD error, const string& msg)
        : runtime_error(FormatErrorMessage(error, msg)), m_error(error) { }

    DWORD GetErrorCode() const { return m_error; }
};

void ThrowLastErrorIf(bool expression, const string& msg)
{
    if (expression) {
        throw Win32Exception(GetLastError(), msg);
    }
}

class File
{
private:
    HANDLE m_handle;

    // Declared but not defined, to avoid double closing.
    File& operator=(const File&);
    File(const File&);
public:
    explicit File(const string& filename)
    {
        m_handle = CreateFileA(filename.c_str(), GENERIC_READ, FILE_SHARE_READ,
            nullptr, OPEN_EXISTING, FILE_ATTRIBUTE_READONLY, nullptr);
        ThrowLastErrorIf(m_handle == INVALID_HANDLE_VALUE,
            "CreateFile call failed on file named " + filename);
    }

    ~File() { CloseHandle(m_handle); }

    HANDLE GetHandle() { return m_handle; }
};

size_t GetFileSizeSafe(const string& filename)
{
    File fobj(filename);
    LARGE_INTEGER filesize;

    BOOL result = GetFileSizeEx(fobj.GetHandle(), &filesize);
    ThrowLastErrorIf(result == FALSE, "GetFileSizeEx failed: " + filename);

    if (filesize.QuadPart < (numeric_limits<size_t>::max)()) {
        return filesize.QuadPart;
    } else {
        throw;
    }
}

vector<char> ReadFileVector(const string& filename)
{
    File fobj(filename);
    size_t filesize = GetFileSizeSafe(filename);
    DWORD bytesRead = 0;

    vector<char> readbuffer(filesize);

    BOOL result = ReadFile(fobj.GetHandle(), readbuffer.data(), readbuffer.size(),
        &bytesRead, nullptr);
    ThrowLastErrorIf(result == FALSE, "ReadFile failed: " + filename);

    cout << filename << " file size: " << filesize << ", bytesRead: "
        << bytesRead << endl;

    return readbuffer;
}

bool IsFileDiff(const string& filename1, const string& filename2)
{
    return ReadFileVector(filename1) != ReadFileVector(filename2);
}

#include <iomanip>

int main ( int argc, char* argv[] )
{
    string filename1("file1.txt");
    string filename2("file2.txt");

    try
    {
        if(argc > 2) {
            filename1 = argv[1];
            filename2 = argv[2];
        }

        cout << "Using file names " << filename1 << " and " << filename2 << endl;

        if (IsFileDiff(filename1, filename2)) {
            cout << "+++ Files are different." << endl;
        } else {
            cout<< "=== Files match." << endl;
        }
    }
    catch(const Win32Exception& e)
    {
        ios state(nullptr);
        state.copyfmt(cout);
        cout << e.what() << endl;
        cout << "Error code: 0x" << hex << uppercase << setw(8) << setfill('0')
            << e.GetErrorCode() << endl;
        cout.copyfmt(state); // restore previous formatting
    }
}
```

## <a name="calling-exceptional-code-from-non-exceptional-code"></a>비 예외 코드에서 예외 코드 호출

"extern C"로 선언된 C++ 함수가 C 프로그램에서 호출됩니다. 여러 다른 언어로 작성된 코드에서 C++ COM 서버를 사용할 수 있습니다. 비예외 코드로 호출되는 C++의 공용 예외 인식 함수를 구현하는 경우 C++ 함수에서는 호출자에 예외를 다시 전파하지 않아야 합니다. 따라서 C++ 함수에서는 처리하는 방법을 알고 있는 모든 예외를 특별히 catch해야 하며, 필요한 경우 예외를 호출자가 인식하는 오류 코드로 변환해야 합니다. 일부 잠재적 예외를 알지 못하는 경우 C++ 함수에는 마지막 처리기로 `catch(...)` 블록이 있어야 합니다. 이러한 경우 프로그램의 상태를 알 수 없으므로 호출자에게 심각한 오류를 보고하는 것이 가장 좋습니다.

다음 예제에서는 throw될 수 있는 예외가 `std::exception`에서 파생된 예외 형식 또는 Win32Exception임을 가정하는 함수를 보여 줍니다. 함수는 이러한 형식의 예외를 catch하고 호출자에게 Win32 오류 코드로 오류 정보를 전파합니다.

```cpp
BOOL DiffFiles2(const string& file1, const string& file2)
{
    try
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return FALSE;
        }
        return TRUE;
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }

    catch(std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return FALSE;
}
```

예외에서 오류 코드로 변환하는 경우 잠재적인 문제 하나는 대개 예외에서 저장될 수 있는 다양한 정보가 오류 코드에 포함되지 않는다는 점입니다. 이를 해결 하기 위해 **`catch`** throw 될 수 있는 각 예외 형식에 대 한 블록을 제공 하 고, 오류 코드로 변환 되기 전에 예외 정보를 기록 하기 위해 로깅을 수행할 수 있습니다. 이 방법은 여러 함수가 모두 동일한 블록 집합을 사용 하는 경우 많은 코드 반복을 만들 수 있습니다 **`catch`** . 코드 반복을 방지 하는 좋은 방법은 및 블록을 구현 하 **`try`** **`catch`** 고 블록에서 호출 되는 함수 개체를 허용 하는 하나의 개인 유틸리티 함수로 이러한 블록을 리팩터링 하는 것입니다 **`try`** . 각 공용 함수에서 람다 식으로 유틸리티 함수에 코드를 전달합니다.

```cpp
template<typename Func>
bool Win32ExceptionBoundary(Func&& f)
{
    try
    {
        return f();
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }
    catch(const std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return false;
}
```

다음 예제에서는 함수를 정의하는 람다 식을 작성하는 방법을 보여 줍니다. 함수가 람다 식을 사용하여 "인라인"으로 정의될 때 명명된 함수 개체로 작성된 경우 보다 읽기가 쉽습니다.

```cpp
bool DiffFiles3(const string& file1, const string& file2)
{
    return Win32ExceptionBoundary([&]() -> bool
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return false;
        }
        return true;
    });
}
```

람다 식에 대 한 자세한 내용은 [람다 식](lambda-expressions-in-cpp.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[예외 및 오류 처리에 대 한 최신 c + + 모범 사례](errors-and-exception-handling-modern-cpp.md)<br/>
[방법: 예외 안전을 위한 디자인](how-to-design-for-exception-safety.md)<br/>
