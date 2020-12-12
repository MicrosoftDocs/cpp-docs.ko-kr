---
description: '자세한 정보: 링커 도구 오류 LNK1188'
title: 링커 도구 오류 LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: 1bd826c3734d8079b370712ae829a0d0fb1abded
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321841"
---
# <a name="linker-tools-error-lnk1188"></a>링커 도구 오류 LNK1188

BADFIXUPSECTION:: 픽스업 대상 ' symbol '이 잘못 되었습니다. 가능한 길이가 0 인 섹션

VxD 링크를 실행 하는 동안 재배치 대상에 섹션이 없습니다. LINK386 (이전 버전)를 사용 하는 경우에는 단일 길이 섹션과 길이가 0이 아닌 다른 길이 섹션을 결합 하는 데 사용 된 OMF group 레코드 (이전 버전)를 사용 했을 수 있습니다. COFF 형식은 그룹 지시문 및 길이가 0 인 섹션을 지원 하지 않습니다. LINK가이 형식의 OMF 개체를 COFF로 자동으로 변환 하는 경우이 오류가 발생할 수 있습니다.
