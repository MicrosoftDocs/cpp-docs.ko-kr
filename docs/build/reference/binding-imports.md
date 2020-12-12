---
description: '자세한 정보: 바인딩 가져오기'
title: 가져오기 바인딩
ms.date: 11/04/2016
helpviewer_keywords:
- /DELAY:NOBIND linker option
- DELAY:NOBIND linker option
ms.assetid: bb766038-deb1-41b1-bcbc-29a30e8c1e2a
ms.openlocfilehash: 7d1b4374bf1d3340a918f252d80102057febe053
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182712"
---
# <a name="binding-imports"></a>가져오기 바인딩

기본 링커 동작은 지연 로드 된 DLL에 대 한 바인딩 가능한 가져오기 주소 테이블을 만드는 것입니다. DLL이 바인딩된 경우 도우미 함수는 참조 되는 각 가져오기에서 **GetProcAddress** 를 호출 하는 대신 바인딩된 정보를 사용 하려고 합니다. 타임 스탬프 또는 기본 설정 주소가 로드 된 DLL의 타임 스탬프 또는 기본 설정 주소와 일치 하지 않으면 도우미 함수는 바인딩된 가져오기 주소 테이블이 오래 된 것으로 가정 하 고 존재 하지 않는 것 처럼 계속 진행 됩니다.

DLL의 지연 로드 된 가져오기를 바인딩하지 않으려는 경우 링커 명령줄에 [/delay](delay-delay-load-import-settings.md): nobind을 지정 하면 바인딩된 가져오기 주소 테이블이 생성 되 고 이미지 파일의 공간이 사용 되지 않습니다.

## <a name="see-also"></a>참고 항목

[Delay-Loaded Dll에 대 한 링커 지원](linker-support-for-delay-loaded-dlls.md)
