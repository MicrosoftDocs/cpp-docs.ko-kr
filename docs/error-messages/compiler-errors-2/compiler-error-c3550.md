---
description: '자세한 정보: 컴파일러 오류 C3550'
title: 컴파일러 오류 C3550
ms.date: 11/04/2016
f1_keywords:
- C3550
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
ms.openlocfilehash: 4cb459e3f8e7fdd0dbb00c1d4dfaa3c3c6b1eb71
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112416"
---
# <a name="compiler-error-c3550"></a>컴파일러 오류 C3550

이 컨텍스트에 일반 'decltype(auto)'만 사용할 수 있습니다.

`decltype(auto)`을 함수 반환 형식의 자리 표시자로 사용하는 경우 자체에서 사용되어야 합니다. 포인터 선언(`decltype(auto*)`), 참조 선언(`decltype(auto&)`) 또는 이러한 기타 모든 한정의 일부로 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

[auto](../../cpp/auto-cpp.md)
