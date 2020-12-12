---
description: '자세한 정보: dllexport, dllimport'
title: dllexport, dllimport
ms.date: 11/04/2016
f1_keywords:
- dllimport_cpp
- dllexport_cpp
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
ms.openlocfilehash: 7147aa07d5579a61a2913fcc0beb85634dc1d8df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195506"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport

**Microsoft 전용**

**`dllexport`** 및 **`dllimport`** 저장소 클래스 특성은 C 및 c + + 언어에 대 한 Microsoft 전용 확장입니다. 이러한 특성을 사용하여 함수, 데이터 및 개체를 DLL에 내보내거나 DLL에서 가져올 수 있습니다.

## <a name="syntax"></a>구문

```
   __declspec( dllimport ) declarator
   __declspec( dllexport ) declarator
```

## <a name="remarks"></a>설명

이러한 특성은 실행 파일이나 다른 DLL일 수 있는 클라이언트에 대한 DLL 인터페이스를 명시적으로 정의합니다. 함수를로 선언 하면 **`dllexport`** 적어도 내보낸 함수 사양과 관련 하 여 모듈 정의 (.def) 파일의 필요성을 없앨 수 있습니다. **`dllexport`** 특성은 **__export** 키워드를 대체 합니다.

클래스가 declspec(dllexport)로 표시된 경우 클래스 계층 구조에 있는 클래스 템플릿의 특수화는 암시적으로 declspec(dllexport)로 표시됩니다. 이는 클래스 템플릿이 명시적으로 인스턴스화되었으며 클래스의 멤버가 정의되어야 함을 의미합니다.

**`dllexport`** 함수의는 데코레이팅된 이름을 사용 하 여 함수를 노출 합니다. C++ 함수의 경우 여기에 이름 변환이 포함됩니다. C 함수 또는 `extern "C"`로 선언된 함수의 경우 여기에 호출 규칙을 기반으로 하는 플랫폼별 데코레이션이 포함됩니다. C/c + + 코드의 이름 데코레이션에 대 한 자세한 내용은 [데코레이팅된 이름](../build/reference/decorated-names.md)을 참조 하세요. `extern "C"`호출 규칙을 사용 하 여 내보낸 c 함수 또는 c + + 함수에는 이름 장식이 적용 되지 않습니다 **`__cdecl`** .

데코레이트되지 않은 이름을 내보내려면 EXPORTS 섹션에서 데코레이트되지 않은 이름을 정의하는 모듈 정의(.def) 파일을 사용하여 연결할 수 있습니다. 자세한 내용은 [내보내기](../build/reference/exports.md)를 참조 하세요. 데코레이팅되지 않은 이름을 내보내는 다른 방법은 `#pragma comment(linker, "/export:alias=decorated_name")` 소스 코드에서 지시문을 사용 하는 것입니다.

**`dllexport`** 또는을 선언할 때 **`dllimport`** 확장 된 [특성 구문](../cpp/declspec.md) 및 키워드를 사용 해야 합니다 **`__declspec`** .

## <a name="example"></a>예제

```cpp
// Example of the dllimport and dllexport class attributes
__declspec( dllimport ) int i;
__declspec( dllexport ) void func();
```

또는 매크로 정의를 사용하여 코드를 보다 읽기 쉽게 만들 수 있습니다.

```cpp
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllImport int j;
DllExport int n;
```

자세한 내용은 다음을 참조하세요.

- [정의 및 선언](../cpp/definitions-and-declarations-cpp.md)

- [Dllexport 및 dllimport를 사용 하 여 인라인 c + + 함수 정의](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

- [일반 규칙 및 제한 사항](../cpp/general-rules-and-limitations.md)

- [C + + 클래스에서 dllimport 및 dllexport 사용](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)
