---
description: pragmaMicrosoft c + +에서 vtordisp에 대 한 자세한 정보
title: vtordisp pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragma, vtordisp
- vtordisp pragma
no-loc:
- pragma
ms.openlocfilehash: f8956aa892aae0472001b007137e6f978d91500e
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713144"
---
# <a name="vtordisp-no-locpragma"></a>`vtordisp` pragma

숨겨진 `vtordisp` 생성/소멸 치환 멤버의 추가를 제어 합니다. 는 `vtordisp` pragma c + +에만 해당 됩니다.

## <a name="syntax"></a>구문

> **`#pragma vtordisp(`**[ **`push,`** ] *n***`)`**\
> **`#pragma vtordisp(pop)`**\
> **`#pragma vtordisp()`**\
> **`#pragma vtordisp(`** [ **`push,`** ] { **`on`** | **`off`** } **`)`**

### <a name="parameters"></a>매개 변수

**`push`**\
`vtordisp`내부 컴파일러 스택에 현재 설정을 푸시하고 새 `vtordisp` 설정을 *n* 으로 설정 합니다.  *N* 을 지정 하지 않으면 현재 `vtordisp` 설정이 변경 되지 않습니다.

**`pop`**\
내부 컴파일러 스택에서 상위 레코드를 제거 하 고 `vtordisp` 설정을 제거 된 값으로 복원 합니다.

*개의*\
설정의 새 값을 지정 합니다 `vtordisp` . 가능한 값은 **`0`** , **`1`** 또는 **`2`** **`/vd0`** 컴파일러 옵션에 해당 **`/vd1`** **`/vd2`** 합니다. 자세한 내용은 [ `/vd` (생성 치환 사용 안 함)](../build/reference/vd-disable-construction-displacements.md)를 참조 하세요.

**`on`**\
`#pragma vtordisp(1)`과 동일합니다.

**`off`**\
`#pragma vtordisp(0)`과 동일합니다.

## <a name="remarks"></a>설명

는 **`vtordisp`** pragma 가상 기본을 사용 하는 코드에만 적용 됩니다. 파생 클래스가 가상 기본 클래스에서 상속 된 가상 함수를 재정의 하 고 파생 클래스의 생성자 또는 소멸자가 가상 기본 클래스에 대 한 포인터를 사용 하 여 해당 함수를 호출 하는 경우 컴파일러는 `vtordisp` 가상 베이스가 있는 클래스에 추가 숨김 필드를 도입할 수 있습니다.

는 뒤에 오는 **`vtordisp`** pragma 클래스의 레이아웃에 영향을 줍니다. **`/vd0`**, **`/vd1`** 및 **`/vd2`** 컴파일러 옵션은 전체 모듈에 대해 동일한 동작을 지정 합니다. **`0`** 숨겨진 멤버를 지정 하거나 표시 하지 **`off`** 않습니다 `vtordisp` . **`vtordisp`** 클래스의 생성자와 소멸자가 포인터가 가리키는 개체에 대해 가상 함수를 호출할 가능성이 없는 경우에만 해제 **`this`** 합니다.

**`1`** 기본적으로 또는를 지정 하면 **`on`** `vtordisp` 필요 없는 숨겨진 멤버가 활성화 됩니다.

**`2`** 을 지정 하면 `vtordisp` 가상 함수를 사용 하는 모든 가상 기본에 대해 숨겨진 멤버를 사용할 수 있습니다. `#pragma vtordisp(2)` 는 **`dynamic_cast`** 부분적으로 생성 된 개체에 대 한의 올바른 성능을 보장 하기 위해 필요할 수 있습니다. 자세한 내용은 [컴파일러 경고 (수준 1) C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)를 참조 하세요.

`#pragma vtordisp()`인수 없이는 `vtordisp` 설정을 초기 설정으로 복원 합니다.

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
