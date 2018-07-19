---
title: 컨테이너 Class::erase | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 368b722f03a68445ddd016705aa8bebc6f33e6f5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842614"
---
# <a name="container-classerase"></a>Container Class::erase

> [!NOTE]
> 이 항목은 C++ 표준 라이브러리에서 사용되는 작동하지 않는 컨테이너 예제로 Visual C++ 설명서에 포함되어 있습니다. 자세한 내용은 [C++ 표준 라이브러리 컨테이너](../standard-library/stl-containers.md)를 참조하세요.

요소를 지웁니다.

## <a name="syntax"></a>구문

```

    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>설명

가 가리키는 제어 된 시퀀스의 요소를 제거 하는 첫 번째 멤버 함수 *_Where*합니다. 두 번째 멤버 함수는 [`first`, `last`]의 범위에서 제어되는 시퀀스의 요소를 제거합니다. 둘 다 제거된 요소 다음에 남아 있는 첫 번째 요소를 지정하는 반복기를 반환하거나, 이러한 요소가 없는 경우 [end](../standard-library/container-class-end.md)를 반환합니다.

복사 작업에서 예외를 throw하는 경우에만 멤버 함수는 예외를 throw합니다.

## <a name="see-also"></a>참고자료

[샘플 컨테이너 클래스](../standard-library/sample-container-class.md)<br/>
