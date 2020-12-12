---
description: '자세한 정보: 링커 도구 오류 LNK1302'
title: 링커 도구 오류 LNK1302
ms.date: 11/04/2016
f1_keywords:
- LNK1302
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
ms.openlocfilehash: 33e9a406cde7910c7340fdfe256711c47eee45cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193697"
---
# <a name="linker-tools-error-lnk1302"></a>링커 도구 오류 LNK1302

안전한 .netmodules 링크만 지원됩니다. .netmodule 파일을 링크할 수 없습니다.

사용자가 MSIL 링크를 호출 하려고 할 때 .netmodule ( **/LN** 으로 컴파일된)이 링커에 전달 되었습니다.  C + + 모듈은 **/clr: safe** 를 사용 하 여 컴파일된 경우 MSIL 링크에 대해 유효 합니다.

이 오류를 해결 하려면 **/clr: safe** 를 사용 하 여 MSIL 링크를 사용 하도록 설정 하거나 모듈 대신 **/clr** 또는 **/clr: pure** .obj 파일을 링커에 전달 합니다.

자세한 내용은 다음을 참조하세요.

- [/LN (MSIL 모듈 만들기)](../../build/reference/ln-create-msil-module.md)

- [링커 입력 파일로 서의 .netmodule 파일](../../build/reference/netmodule-files-as-linker-input.md)
