---
title: Visual C++ 문서 태그의 구분 기호 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe65dfec3befa15ffebde3d074081ee11364f4d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337576"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Visual C++ 문서 태그의 구분 기호
문서 태그를 사용하려면 문서 주석이 시작되고 끝나는 위치를 컴파일러에 알리는 구분 기호가 필요합니다.  
  
 XML 문서 태그에 다음과 같은 종류의 구분 기호를 사용할 수 있습니다.  
  
 `///`  
 문서 예제에 표시되고 Visual C++ 프로젝트 템플릿에 사용되는 형식입니다.  
  
 `/** */`  
 여러 줄 구분 기호입니다.  
  
 `/** */` 구분 기호를 사용할 때 몇 가지 서식 규칙이 있습니다.  
  
-   `/**` 구분 기호가 포함된 줄의 경우, 줄의 나머지 부분이 공백인 경우, 해당 줄은 주석에 대해 처리되지 않습니다. 첫 번째 문자가 공백인 경우, 해당 공백 문자는 무시되고 줄의 나머지 부분이 처리됩니다. 그러지 않으면 `/**` 구분 기호 다음 줄의 전체 텍스트가 주석의 일부로 처리됩니다.  
  
-   `*/` 구분 기호가 포함된 줄의 경우, `*/` 구분 기호까지 공백만 있으면 해당 줄은 무시됩니다. 그러지 않으면 줄의 텍스트가 `*/` 구분 기호까지 주석의 일부로 처리되며, 다음 글머리 기호에서 설명하는 패턴 일치 규칙을 따릅니다.  
  
-   `/**` 구분 기호로 시작하는 줄 다음의 줄의 경우, 컴파일러는 선택적 공백과 별표(`*`)로 구성된 각 줄의 시작 부분에서 더 많은 선택적 공백이 뒤에 오는 공통 패턴을 찾습니다. 컴파일러가 각 줄의 시작 부분에서 공통 문자 집합을 찾으면, `*/` 구분 기호가 있는 줄까지 포함하여 `/**` 구분 기호 뒤의 모든 줄의 패턴을 무시합니다.  
  
 몇 가지 예:  
  
-   다음 주석에서 유일하게 처리되는 부분은 `<summary>`로 시작하는 줄입니다. 다음 두 태그 형식은 동일한 주석을 생성합니다.  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   컴파일러는 " * " 패턴을 적용하여 두 번째 및 세 번째 줄의 시작 부분에서 무시합니다.  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   두 번째 줄에 별표가 없으므로, 컴파일러는 이 주석에서 패턴을 찾을 수 없습니다. 따라서, 두 번째 및 세 번째 줄의 모든 텍스트는 `*/`까지 주석의 일부로 처리됩니다.  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   컴파일러는 두 가지 이유로 이 주석에서 패턴을 찾을 수 없습니다. 첫째, 별표 앞에 일관된 수의 공백으로 시작하는 줄이 없습니다. 둘째, 다섯 번째 줄이 공백과 일치하지 않는 탭으로 시작합니다. 따라서, 두 번째 줄부터 `*/`까지의 모든 텍스트는 주석의 일부로 처리됩니다.  
  
    ```  
    /**  
      * <summary>  
      * text   
     *  text2  
       *  </summary>  
    */  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [XML 문서](../ide/xml-documentation-visual-cpp.md)