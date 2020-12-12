---
description: '자세히 알아보기: 미리 정의 된 규칙'
title: 미리 정의된 규칙
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: 302c649980050764d1bb2f0e9a43b785d0175a09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225832"
---
# <a name="predefined-rules"></a>미리 정의된 규칙

미리 정의 된 유추 규칙은 NMAKE 제공 명령 및 옵션 매크로를 사용 합니다.

|규칙|명령|기본값<br /><br /> action|Batch<br /><br /> 규칙|플랫폼 nmake 실행|
|----------|-------------|------------------------|--------------------|----------------------------|
|.asm.exe|$ (AS) $ (AFLAGS) $<|ml $<|no|x86|
|.asm .obj|$ (AS) $ (AFLAGS)/c $<|ml/c $<|예|x86|
|.asm.exe|$ (AS) $ (AFLAGS) $<|ml64.exe $<|no|X64|
|.asm .obj|$ (AS) $ (AFLAGS)/c $<|ml64.exe/c $<|예|X64|
|.c.exe|$ (CC) $ (CFLAGS) $<|cl $<|no|모두|
|.c .obj|$ (CC) $ (CFLAGS)/c $<|cl/c $<|예|모두|
|.cc.exe|$ (CC) $ (CFLAGS) $<|cl $<|no|모두|
|. 참조 .obj|$ (CC) $ (CFLAGS)/c $<|cl/c $<|예|모두|
|.cpp.exe|$ (CPP) $ (CPPFLAGS) $<|cl $<|no|모두|
|.cpp .obj|$ (CPP) $ (CPPFLAGS)/c $<|cl/c $<|예|모두|
|.cxx.exe|$ (.CXX) $ (CXXFLAGS) $<|cl $<|no|모두|
|. .cxx|$ (.CXX) $ (CXXFLAGS)/c $<|cl/c $<|예|모두|
|.rc .res|$ (RC) $ (RFLAGS)/r $<|rc/r $<|no|모두|

## <a name="see-also"></a>참고 항목

[유추 규칙](inference-rules.md)
