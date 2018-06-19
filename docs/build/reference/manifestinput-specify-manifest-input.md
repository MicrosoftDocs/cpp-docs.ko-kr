---
title: -MANIFESTINPUT (매니페스트 입력 지정) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eecf1740855c2feef0d7cac4bbcc85ad95eade6f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372853"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT(매니페스트 입력 지정)
이미지에 포함 된 매니페스트를 포함 하도록 매니페스트 입력된 파일을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
/MANIFESTINPUT:filename  
```  
  
#### <a name="parameters"></a>매개 변수  
 `filename`  
 매니페스트 파일에 포함 된 매니페스트가 포함입니다.  
  
## <a name="remarks"></a>설명  
 **/MANIFESTINPUT** 옵션은 실행 가능 이미지에 포함 된 매니페스트를 만드는 데 사용할 입력된 파일의 경로 지정 합니다. 여러 매니페스트 입력 파일을 여러 번 스위치를 사용 해야 하는 경우-각 입력된 파일에 대해 한 번씩입니다. 포함 된 매니페스트를 만들려면 매니페스트 입력된 파일은 병합 됩니다. 이 옵션을 사용 하려면는 **/manifest: 포함** 옵션입니다.  
  
 이 옵션에서 직접 설정할 수 없습니다 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]합니다. 대신를 사용 하 여는 **추가 매니페스트 파일** 포함 시킬 추가 매니페스트 파일을 지정 하는 프로젝트의 속성입니다. 자세한 내용은 참조 [입력 및 출력, 매니페스트 도구, 구성 속성 \<프로젝트 이름 > 속성 페이지 대화 상자](../../ide/input-and-output-manifest-tool.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [링커 옵션 설정](../../build/reference/setting-linker-options.md)   
 [링커 옵션](../../build/reference/linker-options.md)