---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4435'
title: 컴파일러 경고(수준 4) C4435
ms.date: 11/04/2016
f1_keywords:
- C4435
helpviewer_keywords:
- C4435
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: ce5ee4e32f6efa1e7986d55fafa0ceec8b754351
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203512"
---
# <a name="compiler-warning-level-4-c4435"></a>컴파일러 경고(수준 4) C4435

'class1': 가상 기본 'class2'(으)로 인해 /vd2의 개체 레이아웃이 변경됩니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

/vd1의 기본 컴파일 옵션으로 파생된 클래스는 표시된 가상 기본 항목에 대해 `vtordisp` 필드를 포함하지 않습니다.  /vd2 또는 `#pragma vtordisp(2)`가 사용된 경우, `vtordisp` 필드가 제공되어 개체 레이아웃을 변경합니다.  그 결과 상호 작용 모듈을 다른 `vtordisp` 설정으로 컴파일할 경우 바이너리 호환성 문제가 발생할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4435를 생성 합니다.

```cpp
// C4435.cpp
// compile with: /c /W4
#pragma warning(default : 4435)
class A
{
public:
    virtual ~A() {}
};

class B : public virtual A  // C4435
{};
```

## <a name="see-also"></a>참고 항목

[vtordisp](../../preprocessor/vtordisp.md)<br/>
[/vd (생성 치환 사용 안 함)](../../build/reference/vd-disable-construction-displacements.md)
