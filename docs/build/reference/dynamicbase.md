---
description: 자세히 알아보기:/DYNAMICBASE
title: /DYNAMICBASE
ms.date: 06/12/2018
f1_keywords:
- /dynamicbase
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
ms.openlocfilehash: 289c0591fa6989d235a63b9bef249078f9a11174
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201055"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Windows Vista에서 처음 사용할 수 있었던 Windows의 ASLR (주소 공간 레이아웃 임의 지정) 기능을 사용 하 여 로드 시 임의로 기준 주소를 지정할 수 있는 실행 가능 이미지를 생성할지 여부를 지정 합니다.

## <a name="syntax"></a>Syntax

> **/DYNAMICBASE**[**: NO**]

## <a name="remarks"></a>설명

**/DYNAMICBASE** 옵션은 *실행 가능한 이미지*(.dll 또는 .exe) 파일의 헤더를 수정 하 여 로드 시 응용 프로그램이 무작위로 기준 주소를 지정 해야 하는지 여부를 나타내고, 힙, 스택 및 기타 운영 체제 할당의 가상 메모리 위치에 영향을 주는 가상 주소 할당 임의 지정을 사용 하도록 설정 합니다. **/DYNAMICBASE** 옵션은 32 비트 및 64 비트 이미지 모두에 적용 됩니다. ASLR은 Windows Vista 이상 운영 체제에서 지원 됩니다. 이 옵션은 이전 운영 체제에서 무시 됩니다.

기본적으로 **/DYNAMICBASE** 가 사용 됩니다. 이 옵션을 사용 하지 않도록 설정 하려면 **/DYNAMICBASE: NO** 를 사용 합니다. [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) 옵션을 적용 하려면 **/DYNAMICBASE** 옵션이 필요 합니다.

## <a name="see-also"></a>참고 항목

- [EDITBIN 옵션](editbin-options.md)
- [Windows ISV 소프트웨어 보안 방어](/previous-versions/bb430720(v=msdn.10))
