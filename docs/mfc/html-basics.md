---
description: '자세한 정보: HTML 기본 사항'
title: HTML 기초
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: f32926beb9152441169320bf3553b0066f78fa7c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290247"
---
# <a name="html-basics"></a>HTML 기초

대부분의 브라우저에는 검색 하는 페이지의 HTML 소스를 검사 하는 기능이 있습니다. 소스를 보면 꺾쇠 괄호 (<>)로 묶인 여러 HTML (하이퍼텍스트 태그 언어) 태그가 텍스트와 함께 표시 됩니다.

아래 단계에서는 HTML 태그를 사용 하 여 간단한 웹 페이지를 만듭니다. 이러한 단계에서는 메모장에서 파일에 일반 텍스트를 입력 하 고, 몇 가지 내용을 변경 하 고, 파일을 저장 하 고, 브라우저에서 페이지를 다시 로드 하 여 변경 내용을 확인 합니다.

#### <a name="to-create-an-html-file"></a>HTML 파일을 만들려면

1. 메모장 또는 일반 텍스트 편집기를 엽니다.

1. **파일** 메뉴에서 **새로 만들기** 를 선택 합니다.

1. 다음 줄을 입력 합니다.

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. **파일** 메뉴에서 **저장** 을 선택 하 고 파일을 c:\webpages\First.htm로 저장 합니다. 편집기에서 파일을 열어 둡니다.

1. 브라우저로 전환 하 고, **파일** 메뉴에서 **열기** 를 선택 하거나, 브라우저의 URL 편집 상자에 *file://C:/webpages/first.htm* 를 입력 합니다. "최상위 HTML 태그" 라는 창 캡션이 있는 빈 페이지가 표시 됩니다.

   태그는 페어링 되며 꺾쇠 괄호에 포함 됩니다. 태그는 대/소문자를 구분 하지 않지만 태그를 표시 하는 데 대/소문자를 사용 하는 경우가 많습니다.

   태그는 \<HTML> 문서를 시작 하 고 태그는 \</HTML> 이를 종료 합니다. 끝 태그 (항상 필수는 아님)는 시작 태그와 동일 하지만 태그 앞에 슬래시 (/)가 있습니다. 꺾쇠 괄호 (<)와 태그의 시작 사이에 공백이 없어야 합니다.

1. 메모장으로 다시 전환 하 고 줄 뒤에 \</HEAD> 다음을 입력 합니다.

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. **파일** 메뉴에서 **저장** 을 선택 합니다.

1. 브라우저로 다시 전환 하 고 페이지를 새로 고칩니다.

   브라우저 창의 클라이언트 영역에 단어가 표시 됩니다. 캐리지 리턴은 무시 됩니다. 줄 바꿈을 포함 하려면 `<BR>` 첫 번째 줄 뒤에 태그를 포함 해야 합니다.

   다음에 나오는 모든 단계에서 및 사이에 텍스트를 삽입 \<BODY> \</BODY> 하 여 문서의 본문에 추가 합니다.

1. 헤더 추가:

    ```html
    <H3>Here's the big picture</H3>
    ```

1. 페이지와 동일한 디렉터리에 저장 된 .gif 파일을 사용 하 여 이미지를 추가 합니다.

    ```html
    <IMG src="yourfile.gif">
    ```

1. 목록 추가:

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. 대신 목록의 번호를 표시 하려면 \<OL> 및 태그 대신 쌍과 태그를 사용 \</OL> \<UL> \</UL> 합니다.

시작 해야 합니다. 웹 페이지에 유용한 기능이 표시 되는 경우 HTML 소스를 검사 하 여 어떻게 만들어졌는지 확인할 수 있습니다. Microsoft Front Page와 같은 HTML 편집기를 사용 하 여 단순 페이지와 고급 페이지를 모두 만들 수 있습니다.

작성 한 파일에 대 한 전체 HTML 소스는 다음과 같습니다.

```html
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

태그, 특성 및 확장에 대 한 자세한 설명은 HTML(Hypertext Markup Language) (HTML) 사양을 참조 하세요.

W3C.org에 [게시 된 최신 버전의 HTML](https://www.w3.org/TR/html/) 입니다.

## <a name="see-also"></a>참고 항목

[MFC 인터넷 프로그래밍 기본 사항](mfc-internet-programming-basics.md)
