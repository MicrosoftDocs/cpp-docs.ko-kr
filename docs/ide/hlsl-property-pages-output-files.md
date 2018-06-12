---
title: 'HLSL 속성 페이지: 출력 파일 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.AssemblerOutputFile
dev_langs:
- C++
ms.assetid: c5ba1e72-30de-43eb-a15a-5b0ae58e55c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd1dc3ba92201567f24aa84ff8dddcd96798b38
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339198"
---
# <a name="hlsl-property-pages-output-files"></a>HLSL 속성 페이지: 출력 파일
HLSL 컴파일러(fxc.exe)의 다음 속성을 구성하려면 해당 **출력 파일** 속성을 사용합니다. HLSL 폴더의 **출력 파일** 속성 페이지에 액세스하는 방법에 대한 자세한 내용은 [프로젝트 속성 작업](../ide/working-with-project-properties.md)을 참조하세요.  
  
## <a name="uielement-list"></a>UI 요소 목록  
 **헤더 변수 이름**  
 HLSL 개체 코드를 인코딩하는 데 사용되는 배열의 이름을 지정합니다. 배열은 HLSL 컴파일러가 출력하는 헤더 파일에 포함됩니다. 헤더 파일의 이름은 **헤더 파일 이름** 속성으로 지정됩니다.  
  
 이 속성은 **/Vn[name]** 명령줄 인수에 해당합니다.  
  
 **헤더 파일 이름**  
 HLSL 컴파일러가 출력하는 헤더 파일의 이름을 지정합니다. 헤더는 배열로 인코딩된 HLSL 개체 코드를 포함합니다. 배열의 이름은 **헤더 변수 이름** 속성으로 지정됩니다.  
  
 이 속성은 **/Fh[name]** 명령줄 인수에 해당합니다.  
  
 **개체 파일 이름**  
 HLSL 컴파일러가 출력하는 개체 파일의 이름을 지정합니다. 기본적으로 이 값은 **$(OutDir)%(Filename).cso**입니다.  
  
 이 속성은 **/Fo[name]** 명령줄 인수에 해당합니다.  
  
 **어셈블러 출력**  
 어셈블리 언어 문만 출력하려면 **어셈블리 전용 목록(/Fc)** 을 사용합니다. **어셈블리 코드 및 16진수(/Fx)** 를 사용하여 어셈블리 언어 문과 해당 op 코드를 모두 16진수로 출력합니다. 기본적으로 목록은 출력되지 않습니다.  
  
 **어셈블러 출력 파일**  
 HLSL 컴파일러가 출력하는 어셈블리 목록 파일의 이름을 지정합니다.  
  
 이 속성은 **/Fc[name]** 및 **/Fx [name]** 명령줄 인수에 해당합니다.  
  
## <a name="see-also"></a>참고 항목  
 [HLSL 속성 페이지](../ide/hlsl-property-pages.md)   
 [HLSL 속성 페이지: 일반](../ide/hlsl-property-pages-general.md)   
 [HLSL 속성 페이지: 고급](../ide/hlsl-property-pages-advanced.md)