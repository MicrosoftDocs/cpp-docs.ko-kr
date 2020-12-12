---
description: '자세한 정보: 링커 도구 경고 LNK4070'
title: 링커 도구 경고 LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: 188c8d88fa4fec332dad80fd5afee346f6099fca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210181"
---
# <a name="linker-tools-warning-lnk4070"></a>링커 도구 경고 LNK4070

/OUT: 파일 이름 지시문 EXP는 ' filename ' 출력 파일 이름과 다릅니다. 지시문 무시

`filename`.Exp 파일이 생성 될 때 [이름](../../build/reference/name-c-cpp.md) 또는 [라이브러리](../../build/reference/library.md) 문에 지정 된은 `filename` 기본적으로 가정 되거나 [/out](../../build/reference/out-output-file-name.md) 옵션으로 지정 된 출력과 다릅니다.

개발 환경에서 출력 파일의 이름을 변경 하 고 프로젝트의 .def 파일이 업데이트 되지 않은 경우이 경고가 표시 됩니다. .Def 파일을 수동으로 업데이트 하 여이 경고를 해결 하십시오.

결과 DLL을 사용 하는 클라이언트 프로그램에서 문제가 발생할 수 있습니다.
