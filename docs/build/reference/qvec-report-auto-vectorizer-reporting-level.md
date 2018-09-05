---
title: -Qvec-report (자동 벡터화 도우미 보고 수준) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85f9d1c63f41b28982018bbe4507ff6bf87158fb
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685855"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report(자동 벡터화 도우미 보고 수준)
컴파일러의 보고 기능을 사용 하도록 설정 [자동 벡터화 도우미](../../parallel/auto-parallelization-and-auto-vectorization.md) 컴파일하는 동안 출력에 대 한 정보 메시지의 수준을 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
/Qvec-report:{1}{2}  
```  
  
## <a name="remarks"></a>설명  
 **/ Qvec-보고서: 1**  
 For 루프 벡터화 되는 정보 메시지를 출력 합니다.  
  
 **/ Qvec-보고서: 2**  
 For 루프는 벡터화 되지 않은, 이유 코드와 함께 하는 for 루프 벡터화 되는 정보 메시지를 출력 합니다.  
  
 이유 코드 및 메시지에 대 한 정보를 참조 하세요 [벡터화 도우미 및 평행 화 도우미 메시지](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)합니다.  
  
### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Visual Studio에서 /Qvec-report 컴파일러 옵션을 설정 하려면  
  
1.  **솔루션 탐색기**에서 프로젝트의 바로 가기 메뉴를 열고 **속성**을 선택합니다.  
  
2.  에 **속성 페이지** 대화 상자의 **C/c + +** 를 선택 **명령줄**합니다.  
  
3.  에 **추가 옵션** 상자에 입력 합니다 `/Qvec-report:1` 또는 `/Qvec-report:2`합니다.  
  
### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>/Qvec-report 컴파일러 옵션을 프로그래밍 방식으로 설정 하려면  
  
-   <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>에 있는 코드 예제를 사용합니다.  
  
## <a name="see-also"></a>참고 항목  
 [/Q 옵션 (하위 수준 작업)](../../build/reference/q-options-low-level-operations.md)   
 [컴파일러 옵션](../../build/reference/compiler-options.md)   
 [컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)   
 [네이티브 코드의 병렬 프로그래밍](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)