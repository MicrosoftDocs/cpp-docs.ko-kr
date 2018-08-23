---
title: -ZW (Windows 런타임 컴파일) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.CompileAsWinRT
- /zw
dev_langs:
- C++
helpviewer_keywords:
- /ZW
- -ZW compiler option
- /ZW compiler option
- -ZW
- Windows Runtime compiler option
ms.assetid: 0fe362b0-9526-498b-96e0-00d7a965a248
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97a97158dda886a09fb6ccb00898a8c518d8e250
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602264"
---
# <a name="zw-windows-runtime-compilation"></a>/ZW(Windows Runtime 컴파일)
컴파일을 지원 하도록 소스 코드 Visual c + + 구성 요소 확장의 C + + 유니버설 Windows 플랫폼 (UWP) 앱을 만들 CX 합니다.  
  
 사용 하는 경우 **/ZW** 컴파일하려면를 항상 지정 **/EHsc** 도 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
/ZW /EHsc  
/ZW:nostdlib /EHsc  
```  
  
## <a name="arguments"></a>인수  
 nostdlib  
 Platform.winmd, Windows.Foundation.winmd 및 기타 기본 Windows 메타데이터(.winmd) 파일이 컴파일에 자동으로 포함되지 않음을 나타냅니다. 대신 사용 해야 합니다는 [/FU (Name Forced #using 파일)](../../build/reference/fu-name-forced-hash-using-file.md) 컴파일러 옵션을 명시적으로 Windows 메타 데이터 파일을 지정 합니다.  
  
## <a name="remarks"></a>설명  
 지정 하는 경우는 **/ZW** 옵션, 컴파일러는 이러한 기능을 지원 합니다.  
  
-   필수 메타 데이터 파일, 네임 스페이스, 데이터 형식 및 함수는 Windows 런타임에서 실행 하는 데 필요한 앱입니다.  
  
-   Windows 런타임 개체의 참조 횟수 및 해당 참조 횟수가 0이 되 면 개체의 삭제 자동 자동입니다.  
  
 Incremental linker를 사용 하 여.obj 파일에 포함 된 Windows 메타 데이터를 지원 하지 않으므로 합니다 **/ZW** 옵션을 합니다 [/Gm (최소 다시 빌드 사용)](../../build/reference/gm-enable-minimal-rebuild.md) 옵션이 호환 되지 않습니다. **/ZW** .  
  
 자세한 내용은 [Visual c + + 언어 참조](../../cppcx/visual-c-language-reference-c-cx.md)합니다.  
  
## <a name="requirements"></a>요구 사항  
  
## <a name="see-also"></a>참고 항목  
 [컴파일러 옵션](../../build/reference/compiler-options.md)   
 [컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)