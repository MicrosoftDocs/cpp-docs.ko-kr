---
description: '자세한 정보: 링커 도구 오류 LNK1241'
title: 링커 도구 오류 LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: abc72b70af9ab694744a91a8789207055bd1a5bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193931"
---
# <a name="linker-tools-error-lnk1241"></a>링커 도구 오류 LNK1241

' 리소스 파일 ' 리소스 파일을 이미 지정 했습니다.

이 오류는 명령줄에서 **cvtres** 를 수동으로 실행 하 고 결과 .obj 파일을 다른 .res 파일 뿐만 아니라 링커에 전달할 경우에 생성 됩니다.

.Res 파일을 여러 개 지정 하려면 **cvtres** 에 의해 생성 된 .obj 파일 내에서가 아닌 .res 파일로 링커에 모두 전달 합니다.
