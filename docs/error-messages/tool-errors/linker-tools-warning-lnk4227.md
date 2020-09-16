---
title: 링커 도구 경고 LNK4227
ms.date: 11/04/2016
f1_keywords:
- LNK4227
helpviewer_keywords:
- LNK4227
ms.assetid: 941a0414-9964-4e02-8487-f9daa42ef7f9
ms.openlocfilehash: 7ac3ef2b6ad8f05a454dafe5e6a7ea0abc07a066
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685491"
---
# <a name="linker-tools-warning-lnk4227"></a>링커 도구 경고 LNK4227

> 메타 데이터 작업 경고 (*HRESULT*): *warning_message*

병합할 때 링커는 메타 데이터 차이를 검색 했습니다.

- 현재 빌드되는 어셈블리를 포함 하는 하나 이상의 참조 된 어셈블리입니다.

- 컴파일에서 하나 이상의 소스 코드 파일입니다.

예를 들어 이름이 같지만 매개 변수 정보를 다르게 선언 (즉, 모든 compilands에서 선언이 일치 하지 않는) 두 개의 전역 함수가 있는 경우 LNK4227이 발생할 수 있습니다. 각 .obj 파일에서 ildasm.exe/TEXT/METADATA *object_file* 를 사용 하 여 형식이 어떻게 다른 지 확인 합니다.

LNK4227는 다른 도구를 사용 하 여 발생 하는 문제를 보고 하는 데도 사용 됩니다. 자세한 내용은 경고 메시지를 검색 하십시오.

경고를 해결 하려면 메타 데이터 문제를 수정 해야 합니다.

## <a name="examples"></a>예제

LNK4227는 참조 된 어셈블리가 해당 어셈블리를 참조 하는 어셈블리와 다르게 서명 된 경우에 생성 됩니다.

다음 샘플에서는 LNK4227를 생성 합니다.

```cpp
// LNK4227.cpp
// compile with: /clr
using namespace System::Reflection;

[assembly:AssemblyDelaySignAttribute(false)];

int main() {}
```

그런 다음

```cpp
// LNK4227b.cpp
// compile with: /clr LNK4227.cpp /FeLNK4227b.exe
using namespace System::Reflection;
using namespace System::Runtime::CompilerServices;

[assembly:AssemblyDelaySignAttribute(true)];
// Try the following line instead
// [assembly:AssemblyDelaySignAttribute(false)];

ref class MyClass
{
};
```

잘못 된 형식의 버전 번호를 어셈블리 특성에 전달 하는 경우에도 LNK4227을 생성할 수 있습니다.  ' * ' 표기법은에만 적용 됩니다 `AssemblyVersionAttribute` .  이 경고를 해결 하려면 이외의 버전 특성에 숫자만 사용 `AssemblyVersionAttribute` 합니다.

다음 샘플에서는 LNK4227를 생성 합니다.

```cpp
// LNK4227e.cpp
// compile with: /clr /LD /W1
using namespace System::Reflection;
[assembly:AssemblyVersionAttribute("2.3.*")];   // OK
[assembly:AssemblyFileVersionAttribute("2.3.*")];   // LNK4227
// try the following line instead
// [assembly:AssemblyFileVersionAttribute("2.3")];
```
