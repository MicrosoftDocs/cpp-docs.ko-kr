---
description: '자세한 정보: DEF 파일을 사용하여 가져오기'
title: DEF 파일을 사용하여 가져오기
ms.date: 11/04/2016
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
ms.openlocfilehash: 9eb4face47bf999daa8f969282cc621708a76006
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156153"
---
# <a name="importing-using-def-files"></a>DEF 파일을 사용하여 가져오기

.def 파일과 함께 **`__declspec(dllimport)`** 을 사용하도록 선택하는 경우 CONSTANT 대신 DATA를 사용하도록 .def 파일을 변경하여 잘못된 코딩으로 인해 문제가 발생할 가능성을 줄여야 합니다.

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

다음 표에서는 이유를 보여 줍니다.

|키워드|가져오기 라이브러리에서 내보내기|내보내기|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

**`__declspec(dllimport)`** 및 CONSTANT를 사용하면 명시적 연결을 허용하도록 만들어진 .lib DLL 가져오기 라이브러리에서 `imp` 버전과 데코레이트되지 않은 이름이 모두 나열됩니다. **`__declspec(dllimport)`** 및 DATA를 사용하면 이름의 `imp` 버전만 나열됩니다.

CONSTANT를 사용하는 경우 다음 코드 구문 중 하나를 사용하여 `ulDataInDll`에 액세스할 수 있습니다.

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-또는-

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

그러나 .def 파일에서 DATA를 사용하는 경우에는 다음 정의로 컴파일된 코드만 `ulDataInDll` 변수에 액세스할 수 있습니다.

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

CONSTANT를 사용하는 경우 추가 수준의 간접 참조를 사용하는 것을 잊으면 변수 자체가 아니라 변수를 가리키는 가져오기 주소 테이블의 포인터에 액세스할 수 있으므로 더 위험합니다. 가져오기 주소 테이블은 현재 컴파일러와 링커에서 읽기 전용으로 만들어지므로 이런 유형의 문제는 종종 액세스 위반으로 나타날 수 있습니다.

현재 MSVC 링커는 .def 파일에서 CONSTANT를 확인하면 이 경우를 설명하기 위해 경고를 실행합니다. 실제로 CONSTANT를 사용하는 이유는 헤더 파일의 프로토타입에 **`__declspec(dllimport)`** 이 나열되어 있지 않은 일부 개체 파일을 다시 컴파일할 수 없는 경우뿐입니다.

## <a name="see-also"></a>참조

[애플리케이션으로 가져오기](importing-into-an-application.md)
