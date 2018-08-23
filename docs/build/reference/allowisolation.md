---
title: -ALLOWISOLATION | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9511ce2d94a426756581b87d863051da25a627b
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2018
ms.locfileid: "42572222"
---
# <a name="allowisolation"></a>/ALLOWISOLATION
매니페스트 조회 동작을 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>설명  
 **/ALLOWISOLATION** 매니페스트 조회 및 로드가 수행 하려면 운영 체제입니다.  
  
 **/ALLOWISOLATION** 가 기본값입니다.  
  
 **/ALLOWISOLATION:NO** 는 매니페스트 및 원인 없습니다 것 처럼 실행 파일이 로드 됩니다 [EDITBIN 참조](../../build/reference/editbin-reference.md) 설정 하는 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` 선택적인 헤더의 비트 `DllCharacteristics` 필드입니다.  
  
 실행 파일에 대해 격리가 비활성화되었으면 Windows 로더가 새로 생성되는 프로세스에 대해 응용 프로그램 매니페스트를 찾으려고 시도하지 않습니다. 실행 파일 자체에 매니페스트가 없거나 이름을 가진 경우 매니페스트가 있더라도 새 프로세스에는 기본 활성화 컨텍스트가 없는 *실행 파일 이름*. exe.manifest 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [EDITBIN 옵션](../../build/reference/editbin-options.md)   
 [/ALLOWISOLATION (매니페스트 조회)](../../build/reference/allowisolation-manifest-lookup.md)   
 [매니페스트 파일 참조](/windows/desktop/SbsCs/manifest-files-reference)