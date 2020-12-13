---
description: '자세한 정보: 심각한 오류 C1092'
title: 심각한 오류 C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: b2a16991784b901202e5d51c0d256ad48305f55f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145134"
---
# <a name="fatal-error-c1092"></a>심각한 오류 C1092

편집하며 계속하기는 데이터 형식에 대한 변경 내용은 지원하지 않습니다. 빌드해야 합니다.

마지막으로 성공한 빌드 이후 데이터 형식을 변경 하거나 추가 했습니다.

- 편집 하며 계속 하기는 클래스, 구조체 또는 열거형 정의를 비롯 한 기존 데이터 형식에 대 한 변경 내용을 지원 하지 않습니다. 디버깅을 중지 하 고 응용 프로그램을 빌드해야 합니다.

- Vc *x* 0 .pdb ( *x* 는 사용 중인 Visual C++의 주 버전)와 같은 프로그램 데이터베이스 파일이 읽기 전용인 경우 편집 하며 계속 하기에서는 새 데이터 형식을 추가할 수 없습니다. 데이터 형식을 추가 하려면 컴파일러에서 .pdb 파일을 쓰기 모드로 열어야 합니다.

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>현재 디버그 세션을 끝내 지 않고이 오류를 제거 하려면

1. 데이터 형식을 오류가 발생하기 이전 상태로 다시 변경합니다.

1. **디버그** 메뉴에서 **코드 변경 내용 적용** 을 선택합니다.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>소스 코드를 변경하지 않고 이 오류를 제거하려면

1. **디버그** 메뉴에서 **디버깅 중지** 를 선택합니다.

1. **빌드** 메뉴에서 **빌드** 를 선택합니다.

자세한 내용은 [지원되는 코드 변경](/visualstudio/debugger/supported-code-changes-cpp)을 참조하세요.
