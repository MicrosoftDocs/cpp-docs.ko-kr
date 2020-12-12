---
description: '자세한 정보: 컴파일러 오류 C2567'
title: 컴파일러 오류 C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: 113dfebc1ac6bde6857ea55fd6249fff12c9faae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209115"
---
# <a name="compiler-error-c2567"></a>컴파일러 오류 C2567

' file '에서 메타 데이터를 열 수 없습니다. 파일이 삭제 되었거나 이동 되었을 수 있습니다.

컴파일러의 프런트 엔드 프로세스에서와 같이 소스 ()에서 참조 된 메타 데이터 파일이 `#using` 컴파일러 백 엔드 프로세스에 의해 동일한 디렉터리에 없습니다. 자세한 내용은 [#using 지시문](../../preprocessor/hash-using-directive-cpp.md) 을 참조 하십시오.

한 컴퓨터에서 **/c** 를 사용 하 여 컴파일한 후 다른 컴퓨터에서 링크 타임 코드 생성을 시도 하는 경우 C2567 발생할 수 있습니다. 자세한 내용은 [/ltcg (링크 타임 코드 생성)](../../build/reference/ltcg-link-time-code-generation.md))를 참조 하세요.

또한 컴퓨터에 메모리가 더 이상 없음을 나타낼 수 있습니다.

이 오류를 해결 하려면 빌드 프로세스의 모든 단계에 대해 메타 데이터 파일이 동일한 디렉터리 위치에 있어야 합니다.
