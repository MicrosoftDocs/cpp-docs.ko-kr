---
description: 다음에 대 한 자세한 정보:/INTEGRITYCHECK
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: b1ea8275bdb356febcf18a2a55b6ab718d8eea96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199664"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

로드 시 이진 이미지의 디지털 서명을 확인 하도록 지정 합니다.

> **/INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>설명

DLL 파일 또는 실행 파일의 헤더에서이 옵션은 메모리 관리자가 Windows에서 이미지를 로드 하는 데 디지털 서명 확인이 필요한 플래그를 설정 합니다. Windows Vista 이전의 Windows 버전은이 플래그를 무시 합니다. 이 옵션은 커널 모드 코드를 구현 하는 64 비트 Dll에 대해 설정 해야 하며 모든 장치 드라이버에 권장 됩니다. 자세한 내용은 [커널 모드 코드 서명 요구 사항](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](editbin-options.md)
