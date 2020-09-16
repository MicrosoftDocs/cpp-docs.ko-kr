---
title: 컴파일러 경고(수준 1) C4691
ms.date: 11/04/2016
f1_keywords:
- C4691
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
ms.openlocfilehash: 6a4d1de621983794acfae4de7707ba127df9a1b7
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685569"
---
# <a name="compiler-warning-level-1-c4691"></a>컴파일러 경고(수준 1) C4691

' type ': 참조 된 형식이 참조 되지 않은 어셈블리 ' file '에 있어야 하는데 대신 사용 되는 현재 변환 단위에 정의 된 형식입니다.

원래 형식 정의를 포함 하는 메타 데이터 파일을 참조 하지 않고 컴파일러에서 로컬 형식 정의를 사용 하 고 있습니다.

*파일*을 다시 작성 하는 경우 pragma [warning](../../preprocessor/warning.md)을 사용 하 여 C4691를 무시 하거나 해제할 수 있습니다.  즉, 빌드하는 파일이 컴파일러에서 형식 정의를 찾을 것으로 예상 하는 파일과 동일한 경우 C4691를 무시할 수 있습니다.

그러나 컴파일러에서 메타 데이터에서 참조 되는 동일한 어셈블리의 정의를 사용 하는 경우 예기치 않은 동작이 발생할 수 있습니다. CLR 형식은 형식의 이름 뿐만 아니라 어셈블리 에서도 형식화 됩니다.  즉, 어셈블리 z.dll의 형식 Z는 어셈블리 y.dll의 형식 Z와 다릅니다.

## <a name="examples"></a>예제

이 샘플에는 원래 유형 정의가 포함 되어 있습니다.

```cpp
// C4691_a.cpp
// compile with: /clr /LD /W1
public ref class Original_Type {};
```

이 샘플은 C4691_a.dll를 참조 하 고 Original_Type 형식의 필드를 선언 합니다.

```cpp
// C4691_b.cpp
// compile with: /clr /LD
#using "C4691_a.dll"
public ref class Client {
public:
   Original_Type^ ot;
};
```

다음 샘플에서는 C4691를 생성 합니다.  이 샘플에는 Original_Type에 대 한 정의가 포함 되어 있으며 C4691a.dll를 참조 하지 않습니다.

해결 하려면 원래 형식 정의를 포함 하는 메타 데이터 파일을 참조 하 고 로컬 선언 및 정의를 제거 합니다.

```cpp
// C4691_c.cpp
// compile with: /clr /LD /W1
// C4691 expected

// Uncomment the following line to resolve.
// #using "C4691_a.dll"
#using "C4691_b.dll"

// Delete the following line to resolve.
ref class Original_Type;

public ref class MyClass : Client {};
```
