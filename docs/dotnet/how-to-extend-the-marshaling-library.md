---
description: '자세히 알아보기: 방법: 마샬링 라이브러리 확장'
title: '방법: 마샬링 라이브러리 확장명'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: 829e05002c23f5a5b59efdb5e65dc5769ca7906a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134968"
---
# <a name="how-to-extend-the-marshaling-library"></a>방법: 마샬링 라이브러리 확장명

이 항목에서는 마샬링 라이브러리를 확장 하 여 데이터 형식 간에 더 많은 변환을 제공 하는 방법에 대해 설명 합니다. 사용자는 라이브러리에서 현재 지원 되지 않는 데이터 변환에 대해 마샬링 라이브러리를 확장할 수 있습니다.

[Marshal_context 클래스](../dotnet/marshal-context-class.md)를 사용 하거나 사용 하지 않고 두 가지 방법 중 하나를 사용 하 여 마샬링 라이브러리를 확장할 수 있습니다. 새 변환에 컨텍스트가 필요한 지 여부를 확인 하려면 [c + +의 마샬링 개요](../dotnet/overview-of-marshaling-in-cpp.md) 항목을 검토 하세요.

두 경우 모두, 먼저 새 마샬링 변환을 위한 파일을 만듭니다. 표준 마샬링 라이브러리 파일의 무결성을 유지 하기 위해이 작업을 수행 합니다. 프로젝트를 다른 컴퓨터 또는 다른 프로그래머에 게 이식 하려면 새 마샬링 파일을 나머지 프로젝트와 함께 복사 해야 합니다. 이러한 방식으로 프로젝트를 받는 사용자는 새 변환을 받게 되며 라이브러리 파일을 수정할 필요가 없습니다.

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>컨텍스트가 필요 하지 않은 변환으로 마샬링 라이브러리를 확장 하려면

1. 새 마샬링 함수를 저장할 파일을 만듭니다 (예: MyMarshal. h).

1. 마샬링 라이브러리 파일을 하나 이상 포함 합니다.

   - 기본 형식에 대해 .h를 마샬링합니다.

   - windows 데이터 형식에 대 한 marshal_windows.

   - c + + 표준 라이브러리 데이터 형식에 대 한 marshal_cppstd.

   - ATL 데이터 형식에 대 한 marshal_atl.

1. 이러한 단계 끝에 있는 코드를 사용 하 여 변환 함수를 작성 합니다. 이 코드에서 TO는 변환할 형식입니다 .는에서 변환할 형식입니다 `from` .는 변환 될 매개 변수입니다.

1. 변환 논리에 대 한 주석을 `from` 매개 변수를의 개체로 변환 하 여 변환 된 개체를 입력 하 고 반환 하는 코드로 바꿉니다.

```
namespace msclr {
   namespace interop {
      template<>
      inline TO marshal_as<TO, FROM> (const FROM& from) {
         // Insert conversion logic here, and return a TO parameter.
      }
   }
}
```

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>컨텍스트를 필요로 하는 변환을 사용 하 여 마샬링 라이브러리를 확장 하려면

1. 새 마샬링 함수를 저장할 파일을 만듭니다 (예: MyMarshal. h).

1. 마샬링 라이브러리 파일을 하나 이상 포함 합니다.

   - 기본 형식에 대해 .h를 마샬링합니다.

   - windows 데이터 형식에 대 한 marshal_windows.

   - c + + 표준 라이브러리 데이터 형식에 대 한 marshal_cppstd.

   - ATL 데이터 형식에 대 한 marshal_atl.

1. 이러한 단계 끝에 있는 코드를 사용 하 여 변환 함수를 작성 합니다. 이 코드에서 TO는 변환할 형식입니다 .는에서 변환할 형식입니다 `toObject` .는 결과를 저장할 포인터이 고은 `fromObject` 변환할 매개 변수입니다.

1. 코드를 초기화 하는 방법에 대 한 주석을 `toPtr` 적절 한 빈 값으로 초기화 하는 주석을 바꿉니다. 예를 들어 포인터가 포인터인 경우로 설정 `NULL` 합니다.

1. 변환 논리에 대 한 주석을 `from` 매개 변수를 형식의 개체로 변환 하는 코드로 바꿉니다  . 변환 된이 개체는에 저장 됩니다 `toPtr` .

1. 설정에 대 한 주석을 `toObject` 변환 된 개체로 설정 하는 코드로 바꿉니다 `toObject` .

1. 에 의해 할당 된 메모리를 해제 하는 코드를 사용 하 여 네이티브 리소스 정리에 대 한 설명을 바꿉니다 `toPtr` . `toPtr`를 사용 하 여 메모리 **`new`** 를 할당 한 경우를 사용 하 여 메모리를 **`delete`** 해제 합니다.

```
namespace msclr {
   namespace interop {
      template<>
      ref class context_node<TO, FROM> : public context_node_base
      {
      private:
         TO toPtr;
      public:
         context_node(TO& toObject, FROM fromObject)
         {
            // (Step 4) Initialize toPtr to the appropriate empty value.
            // (Step 5) Insert conversion logic here.
            // (Step 6) Set toObject to the converted parameter.
         }
         ~context_node()
         {
            this->!context_node();
         }
      protected:
         !context_node()
         {
            // (Step 7) Clean up native resources.
         }
      };
   }
}
```

## <a name="example-extend-marshaling-library"></a>예: 마샬링 라이브러리 확장

다음 예제에서는 컨텍스트가 필요 하지 않은 변환으로 마샬링 라이브러리를 확장 합니다. 이 예제에서 코드는 직원 정보를 네이티브 데이터 형식에서 관리 되는 데이터 형식으로 변환 합니다.

```cpp
// MyMarshalNoContext.cpp
// compile with: /clr
#include <msclr/marshal.h>

value struct ManagedEmp {
   System::String^ name;
   System::String^ address;
   int zipCode;
};

struct NativeEmp {
   char* name;
   char* address;
   int zipCode;
};

namespace msclr {
   namespace interop {
      template<>
      inline ManagedEmp^ marshal_as<ManagedEmp^, NativeEmp> (const NativeEmp& from) {
         ManagedEmp^ toValue = gcnew ManagedEmp;
         toValue->name = marshal_as<System::String^>(from.name);
         toValue->address = marshal_as<System::String^>(from.address);
         toValue->zipCode = from.zipCode;
         return toValue;
      }
   }
}

using namespace System;
using namespace msclr::interop;

int main() {
   NativeEmp employee;

   employee.name = "Jeff Smith";
   employee.address = "123 Main Street";
   employee.zipCode = 98111;

   ManagedEmp^ result = marshal_as<ManagedEmp^>(employee);

   Console::WriteLine("Managed name: {0}", result->name);
   Console::WriteLine("Managed address: {0}", result->address);
   Console::WriteLine("Managed zip code: {0}", result->zipCode);

   return 0;
}
```

이전 예제에서 `marshal_as` 함수는 변환 된 데이터에 대 한 핸들을 반환 합니다. 데이터의 추가 복사본을 만들지 않도록 하기 위해이 작업이 수행 되었습니다. 변수를 직접 반환 하면 이와 관련 된 불필요 한 성능 비용이 발생 합니다.

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example-convert-employee-information"></a>예: 직원 정보 변환

다음 예에서는 employee 정보를 관리 되는 데이터 형식에서 네이티브 데이터 형식으로 변환 합니다. 이 변환에는 마샬링 컨텍스트가 필요 합니다.

```cpp
// MyMarshalContext.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr/marshal.h>

value struct ManagedEmp {
   System::String^ name;
   System::String^ address;
   int zipCode;
};

struct NativeEmp {
   const char* name;
   const char* address;
   int zipCode;
};

namespace msclr {
   namespace interop {
      template<>
      ref class context_node<NativeEmp*, ManagedEmp^> : public context_node_base
      {
      private:
         NativeEmp* toPtr;
         marshal_context context;
      public:
         context_node(NativeEmp*& toObject, ManagedEmp^ fromObject)
         {
            // Conversion logic starts here
            toPtr = NULL;

            const char* nativeName;
            const char* nativeAddress;

            // Convert the name from String^ to const char*.
            System::String^ tempValue = fromObject->name;
            nativeName = context.marshal_as<const char*>(tempValue);

            // Convert the address from String^ to const char*.
            tempValue = fromObject->address;
            nativeAddress = context.marshal_as<const char*>(tempValue);

            toPtr = new NativeEmp();
            toPtr->name = nativeName;
            toPtr->address = nativeAddress;
            toPtr->zipCode = fromObject->zipCode;

            toObject = toPtr;
         }
         ~context_node()
         {
            this->!context_node();
         }
      protected:
         !context_node()
         {
            // When the context is deleted, it will free the memory
            // allocated for toPtr->name and toPtr->address, so toPtr
            // is the only memory that needs to be freed.
            if (toPtr != NULL) {
               delete toPtr;
               toPtr = NULL;
            }
         }
      };
   }
}

using namespace System;
using namespace msclr::interop;

int main() {
   ManagedEmp^ employee = gcnew ManagedEmp();

   employee->name = gcnew String("Jeff Smith");
   employee->address = gcnew String("123 Main Street");
   employee->zipCode = 98111;

   marshal_context context;
   NativeEmp* result = context.marshal_as<NativeEmp*>(employee);

   if (result != NULL) {
      printf_s("Native name: %s\nNative address: %s\nNative zip code: %d\n",
         result->name, result->address, result->zipCode);
   }

   return 0;
}
```

```Output
Native name: Jeff Smith
Native address: 123 Main Street
Native zip code: 98111
```

## <a name="see-also"></a>참고 항목

[C + +의 마샬링 개요](../dotnet/overview-of-marshaling-in-cpp.md)
