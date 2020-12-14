---
description: '자세한 정보: 링커 도구 오류 LNK2027'
title: 링커 도구 오류 LNK2027
ms.date: 11/04/2016
f1_keywords:
- LNK2027
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
ms.openlocfilehash: 006ca3b0c9d0ef85f118db9b562e8228c7cad238
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275765"
---
# <a name="linker-tools-error-lnk2027"></a>링커 도구 오류 LNK2027

확인 되지 않은 모듈 참조 ' module '

링커에 전달 된 파일이 **/ASSEMBLYMODULE** 로 지정 되지 않고 링커에 직접 전달 되지 않은 모듈에 대 한 종속성이 있습니다.

LNK2027를 해결 하려면 다음 중 하나를 수행 합니다.

- 모듈 종속성이 있는 파일을 링커에 전달 하지 마십시오.

- **/ASSEMBLYMODULE** 를 사용 하 여 모듈을 지정 합니다.

- 모듈이 안전한 .netmodule인 경우 모듈을 링커에 직접 전달합니다.

자세한 내용은 [/ASSEMBLYMODULE (MSIL 모듈을 어셈블리에 추가)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) 및 [.Netmodule 파일을 링커 입력으로](../../build/reference/netmodule-files-as-linker-input.md)참조 하세요.
