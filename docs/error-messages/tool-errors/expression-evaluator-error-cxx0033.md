---
description: '자세한 정보: 식 계산기 오류 CXX0033'
title: 식 계산기 오류 CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 714499d8d1bc0812395576fe27be690997982065
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160326"
---
# <a name="expression-evaluator-error-cxx0033"></a>식 계산기 오류 CXX0033

OMF 형식 정보에 오류가 있습니다.

실행 파일에 디버깅을 위한 올바른 OMF (개체 모듈 형식)가 없습니다.

이 오류는 CAN0033와 동일 합니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 이 버전의 Visual C++ 함께 릴리스된 링커를 사용 하 여 실행 파일을 만들지 않았습니다. LINK.exe의 현재 버전을 사용 하 여 개체 코드를 다시 연결 합니다.

1. .Exe 파일이 손상 되었을 수 있습니다. 프로그램을 다시 컴파일하고 다시 링크 합니다.
