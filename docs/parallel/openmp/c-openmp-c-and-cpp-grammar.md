---
description: '자세히 알아보기: C. OpenMP C 및 c + + 문법'
title: C. OpenMP C 및 C++ 문법
ms.date: 01/16/2019
ms.assetid: 97a878ce-1533-47f7-a134-66fcbff48524
ms.openlocfilehash: 9543d721afbff1069b5497ba8dc7092089a1b706
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342506"
---
# <a name="c-openmp-c-and-c-grammar"></a>C. OpenMP C 및 C++ 문법

[C.1 표기법](#c1-notation)<br/>
[C.2 규칙](#c2-rules)

## <a name="c1-notation"></a>C.1 표기법

문법 규칙은 비 터미널의 이름, 콜론, 개별 줄에서 대체 대체 항목으로 구성 됩니다.

구문 식 용어<sub>옵트인</sub> 은 바꾸기 내에서 용어를 선택할 수 있음을 나타냅니다.

구문 식 *용어*<sub>optseq</sub> 는 다음과 같은 추가 규칙을 사용 하 여 *용어-seq*<sub>opt</sub> 와 동일 합니다.

*용어-seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*부채*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*용어-seq* *용어*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*용어-seq* `,` *용어*   

## <a name="c2-rules"></a>C.2 규칙

표기법은 C 표준의 단원 6.1에 설명 되어 있습니다. 이 문법 부록에서는 OpenMP C 및 c + + 지시문의 기본 언어 문법에 대 한 확장을 보여 줍니다.

**/\* c + + (ISO/IEC 14882:1998) \*/**

*문-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 지시문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*문-seq 문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*문-시퀀스 openmp 지시문*

**/\* C90 (ISO/IEC 9899:1990) \*/**

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 지시문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*문 목록 문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*문 목록 openmp 지시문*

**/\* C99 (ISO/IEC 9899:1999) \*/**

*블록 항목*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 지시문*

**/\* 표준 문 \*/**

*statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp 구문*

*openmp 구문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*병렬 생성*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*for 구문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*섹션-구문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*단일 구문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*병렬 구문을 생성 합니다.*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*병렬-섹션-구문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*마스터-구문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*중요 구문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic 구문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*정렬 된 구문*

*openmp 지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*장벽-지시문*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*flush-지시문*

*구조화 된 블록*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*

*병렬 생성*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*병렬 지시문 구조화 된 블록*

*병렬 지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel`*병렬 절*<sub>optseq</sub> *새 줄*

*병렬 절*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*고유-병렬 절*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*데이터 절*

*고유-병렬 절*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `if (`*식*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `num_threads (`*식*   `)`

*구문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*for 지시문 반복-문*

*for 지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp for`*for 절*<sub>optseq</sub> *새 줄*

*for 절*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*고유-절*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*데이터 절*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*고유-절*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `ordered`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (`*일정-종류*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (`*일정-종류* `,` *식*      `)`

*일정-종류*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `static`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `dynamic`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `guided`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `runtime`

*섹션-구문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*섹션-지시어 섹션-범위*

*섹션-지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp sections`*섹션-절*<sub>optseq</sub> *줄 바꿈*

*섹션-절*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*데이터 절*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*섹션 범위*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{섹션 시퀀스}*

*섹션 순서*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*섹션-지시문*<sub>opt</sub> *구조화 된 블록*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*섹션 시퀀스 섹션-지시문 구조 블록*

*섹션-지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp section`*새 줄*

*단일 구문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*단일 지시문 구조화 된 블록*

*단일 지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp single`*단일 절*<sub>optseq</sub> *새 줄*

*단일 절*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*데이터 절*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*병렬 구문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*병렬-지시문 반복-문*

*병렬-지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel for`*병렬-절*<sub>optseq</sub> *새 줄*

*병렬* 처리 방법:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*고유-병렬 절*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*고유-절*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*데이터 절*

*병렬-섹션-구문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*병렬-섹션-지시문 섹션-범위*

*병렬-섹션-지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel sections`*병렬-섹션-절*<sub>optseq</sub> 

*병렬-섹션-절*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*고유-병렬 절*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*데이터 절*

*마스터-구문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*마스터-지시문 구조화 된 블록*

*master-지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp master`*새 줄*

*중요 구문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*임계-지시문 구조화 된 블록*

*중요-지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp critical`*지역 문구*<sub>opt</sub> *new 선*

*지역 구*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*한정자*

*장벽-지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp barrier`*새 줄*

*원자성 구문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*원자성 지시문 식-문*

*원자성 지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp atomic`*새 줄*

*flush-지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp flush`*플러시-변수*<sub>opt</sub> *new-줄*

*플러시-변수*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(변수 목록)*

*정렬 된 구문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*순서가 지정 된 지시문 구조화 된 블록*

*순서가 지정 된 지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp ordered`*새 줄*

**/\* 표준 선언 \*/**

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*threadprivate-지시문*

*threadprivate-지시문*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp threadprivate (`*변수 목록* `)` *새 줄*    

*데이터 절*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `private (`*변수 목록*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyprivate (`  *변수 목록*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `firstprivate (`  *변수 목록*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `lastprivate (`*변수 목록*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `shared (`*변수 목록*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( shared )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( none )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `reduction (`  *감소 연산자* `:` *변수 목록*          `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyin (`  *변수 목록*    `)`

*감소 연산자*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;다음 중 하나입니다.   `+ \* - & ^ | && ||`

**/\* C에서 \*/**

*변수 목록*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*변수 목록* `,` *식별자*   

**/\* c + +에서 \*/**

*변수 목록*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*id 식*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*변수 목록* `,` *id 식*   
