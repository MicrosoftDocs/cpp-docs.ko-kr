---
description: '자세한 정보: 변환: 진단'
title: '변환: 진단'
ms.date: 11/04/2016
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
ms.openlocfilehash: 09fc44dea8d51dbb267d402745c8c2a095b969d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243057"
---
# <a name="translation-diagnostics"></a>변환: 진단

**ANSI 2.1.1.3** 진단 식별 방법

Microsoft C는 다음의 경우에 형식에서 오류 메시지를 생성합니다.

> *filename* **(** *line-number* **) :** *diagnostic* **C**<em>number</em> *message*

여기서 ‘파일 이름’은 오류가 발견된 소스 파일의 이름이고, ‘줄 번호’는 컴파일러 오류가 발견된 줄 번호이고, ‘진단’은 “오류” 또는 “경고”이고, ‘번호’는 오류 또는 경고를 식별하는 고유한 네 자리 숫자(**C** 뒤에 위치, 구문 설명 참조)이고, ‘메시지’는 설명 메시지입니다.     

## <a name="see-also"></a>참조

[구현 정의 ](../c-language/implementation-defined-behavior.md)
