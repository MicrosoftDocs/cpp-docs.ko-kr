---
title: 코드 분석을 위한 샘플 C++ 프로젝트
description: Visual Studio의 Microsoft c + +에 대 한 코드 분석 연습에서 사용할 샘플 솔루션을 만드는 방법입니다.
ms.date: 04/14/2020
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: dd4fe67c05200ccc2865bc7c48b1f5047d77565e
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924623"
---
# <a name="sample-c-project-for-code-analysis"></a>코드 분석을 위한 샘플 C++ 프로젝트

다음 절차에서는 [연습: 오류에 대 한 c/c + + 코드 분석](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)샘플을 만드는 방법을 보여 줍니다. 이 절차에서는 다음을 생성합니다.

- *CppDemo* 라는 Visual Studio 솔루션.

- *Codedefects* 이라는 정적 라이브러리 프로젝트입니다.

- *주석* 이라는 정적 라이브러리 프로젝트입니다.

절차에서는 헤더에 대해 코드를 제공하고, 정적 라이브러리에 대해 *.cpp* 파일을 제공합니다.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>CppDemo 솔루션 및 CodeDefects 프로젝트 만들기

::: moniker range=">=msvc-160"

1. Visual Studio를 열고 **새 프로젝트 만들기** 를 선택 합니다.

1. **새 프로젝트 만들기** 대화 상자에서 언어 필터를 **c + +** 로 변경 합니다.

1. **Windows 바탕 화면 마법사** 를 선택 하 고 **다음** 단추를 선택 합니다.

1. **새 프로젝트 구성** 페이지의 **프로젝트 이름** 텍스트 상자에 *codedefects* 을 입력 합니다.

1. **솔루션 이름** 텍스트 상자에 *CppDemo* 을 입력 합니다.

1. **만들기** 를 선택합니다.

1. **Windows 데스크톱 프로젝트** 대화 상자에서 **응용 프로그램 형식을** **정적 라이브러리 (.lib)** 로 변경 합니다.

1. **추가 옵션** 에서 **빈 프로젝트** 를 선택합니다.

1. **확인** 을 선택 하 여 솔루션 및 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="msvc-150"

1. Visual Studio를 엽니다. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자에서 **Visual C++** > **Windows 데스크톱** 을 선택 합니다.

1. **Windows 바탕 화면 마법사** 를 선택 합니다.

1. **이름** 텍스트 상자에 *codedefects* 을 입력 합니다.

1. **솔루션 이름** 텍스트 상자에 *CppDemo* 을 입력 합니다.

1. **확인** 을 선택합니다.

1. **Windows 데스크톱 프로젝트** 대화 상자에서 **응용 프로그램 형식을** **정적 라이브러리 (.lib)** 로 변경 합니다.

1. **추가 옵션** 에서 **빈 프로젝트** 를 선택합니다.

1. **확인** 을 선택 하 여 솔루션 및 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="msvc-140"

1. Visual Studio를 엽니다. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자에서 **템플릿** > **Visual C++** > **Win32** 를 선택 합니다.

1. **Win32 콘솔 응용 프로그램** 을 선택 합니다.

1. **이름** 텍스트 상자에 *codedefects* 을 입력 합니다.

1. **솔루션 이름** 텍스트 상자에 *CppDemo* 을 입력 합니다.

1. **확인** 을 선택합니다.

1. **Win32 응용 프로그램 마법사** 대화 상자에서 **다음** 단추를 선택 합니다.

1. **응용 프로그램 유형을** **정적 라이브러리로** 변경 합니다.

1. **추가 옵션** 에서 **미리 컴파일된 헤더** 를 선택 취소 합니다.

1. **마침** 을 선택 하 여 솔루션 및 프로젝트를 만듭니다.

::: moniker-end

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>CodeDefects 프로젝트에 헤더 및 원본 파일 추가

1. 솔루션 탐색기에서 **Codedefects** 을 확장 합니다.

1. **헤더 파일** 에 대 한 상황에 맞는 메뉴를 열려면 마우스 오른쪽 단추를 클릭 합니다. **Add**  >  **새 항목** 추가를 선택 합니다.

1. **새 항목 추가** 대화 상자에서 **Visual C++**  >  **코드** 를 선택한 다음 **헤더 파일 (.h)** 을 선택 합니다.

1. **이름** 입력란에 *Bug. h* 를 입력 한 다음 **추가** 단추를 선택 합니다.

1. *버그* 에 대 한 편집 창에서 콘텐츠를 선택 하 고 삭제 합니다.

1. 다음 코드를 복사하여 편집기에서 *Bug.h* 파일에 붙여넣습니다.

    ```cpp
    #pragma once

    #include <windows.h>

    // Function prototypes
    bool CheckDomain(wchar_t const *);
    HRESULT ReadUserAccount();

    // These constants define the common sizes of the
    // user account information throughout the program
    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

1. 솔루션 탐색기에서 마우스 오른쪽 단추를 클릭 하 여 **소스 파일** 에 대 한 상황에 맞는 메뉴를 엽니다. **Add**  >  **새 항목** 추가를 선택 합니다.

1. **새 항목 추가** 대화 상자에서 **C++ 파일(.cpp)** 을 선택합니다.

1. **이름** 입력란에 *버그나* 를 입력 한 다음 **추가** 단추를 선택 합니다.

1. 다음 코드를 복사하여 편집기에서 *Bug.cpp* 파일에 붙여넣습니다.

    ```cpp
    #include "Bug.h"

    // the user account
    wchar_t g_userAccount[USER_ACCOUNT_LEN] = { L"domain\\user" };
    int len = 0;

    bool CheckDomain(wchar_t const* domain)
    {
        return (wcsnlen_s(domain, USER_ACCOUNT_LEN) > 0);
    }

    HRESULT ReadUserAccount()
    {
        return S_OK;
    }

    bool ProcessDomain()
    {
        wchar_t* domain = new wchar_t[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount())
        {
            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
            {
                if (g_userAccount[len] == L'\\')
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete[] domain;
                return false;
            }
            else
            {
                domain[len] = L'\0';
            }
            // Process domain string
            bool result = CheckDomain(domain);

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i + j;
    }
    ```

1. 메뉴 모음에서 **파일**  >  **모두 저장** 을 선택 합니다.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>주석 프로젝트 추가 및 정적 라이브러리로 구성

::: moniker range=">=msvc-160"

1. 솔루션 탐색기에서 **CppDemo** 을 마우스 오른쪽 단추로 클릭 하 여 상황에 맞는 메뉴를 엽니다. **Add**  >  **새 프로젝트** 추가를 선택 합니다.

1. **새 프로젝트 추가** 대화 상자에서 **Windows 바탕 화면 마법사** 를 선택 하 고 **다음** 단추를 선택 합니다.

1. **새 프로젝트 구성** 페이지의 **프로젝트 이름** 입력란에 *주석을* 입력 하 고 **만들기** 를 선택 합니다.

1. **Windows 데스크톱 프로젝트** 대화 상자에서 **응용 프로그램 형식을** **정적 라이브러리 (.lib)** 로 변경 합니다.

1. **추가 옵션** 에서 **빈 프로젝트** 를 선택합니다.

1. **확인** 을 선택하여 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="msvc-150"

1. 솔루션 탐색기에서 **CppDemo** 을 마우스 오른쪽 단추로 클릭 하 여 상황에 맞는 메뉴를 엽니다. **Add**  >  **새 프로젝트** 추가를 선택 합니다.

1. **새 프로젝트 추가** 대화 상자에서 **Visual C++** > **Windows Desktop** 을 선택 합니다.

1. **Windows 바탕 화면 마법사** 를 선택 합니다.

1. **이름** 텍스트 상자에 *주석을* 입력 하 고 **확인** 을 선택 합니다.

1. **Windows 데스크톱 프로젝트** 대화 상자에서 **응용 프로그램 형식을** **정적 라이브러리 (.lib)** 로 변경 합니다.

1. **추가 옵션** 에서 **빈 프로젝트** 를 선택합니다.

1. **확인** 을 선택하여 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="msvc-140"

1. 솔루션 탐색기에서 **CppDemo** 을 마우스 오른쪽 단추로 클릭 하 여 상황에 맞는 메뉴를 엽니다. **Add**  >  **새 프로젝트** 추가를 선택 합니다.

1. **새 프로젝트 추가** 대화 상자에서 **Visual C++** > **Win32** 를 선택 합니다.

1. **Win32 콘솔 응용 프로그램** 을 선택 합니다.

1. **이름** 텍스트 상자에 *주석을* 입력 합니다.

1. **확인** 을 선택합니다.

1. **Win32 응용 프로그램 마법사** 대화 상자에서 **다음** 단추를 선택 합니다.

1. **응용 프로그램 유형을** **정적 라이브러리로** 변경 합니다.

1. **추가 옵션** 에서 **미리 컴파일된 헤더** 를 선택 취소 합니다.

1. **마침** 을 선택하여 프로젝트를 만듭니다.

::: moniker-end

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>주석 프로젝트에 헤더 파일 및 원본 파일 추가

1. 솔루션 탐색기에서 **주석** 을 확장 합니다.

1. **주석** 아래의 **헤더 파일** 에 대 한 상황에 맞는 메뉴를 열려면 마우스 오른쪽 단추를 클릭 합니다. **Add**  >  **새 항목** 추가를 선택 합니다.

1. **새 항목 추가** 대화 상자에서 **Visual C++**  >  **코드** 를 선택한 다음 **헤더 파일 (.h)** 을 선택 합니다.

1. **이름** 입력란에 annotation을 입력 한 다음 **추가** 단추를 선택 합니다 *.*

1. 주석의 편집 창에서 콘텐츠를 선택 하 고 삭제 합니다 *.*

1. 다음 코드를 복사하여 편집기에서 *annotations.h* 파일에 붙여넣습니다.

    ```cpp
    #pragma once
    #include <sal.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    _Ret_maybenull_ LinkedList* AllocateNode();
    ```

1. 솔루션 탐색기에서 마우스 오른쪽 단추를 클릭 하 여 **주석** 아래의 **소스 파일** 에 대 한 상황에 맞는 메뉴를 엽니다. **Add**  >  **새 항목** 추가를 선택 합니다.

1. **새 항목 추가** 대화 상자에서 **C++ 파일(.cpp)** 을 선택합니다.

1. **이름** 입력란에 annotation *을 입력 한* 다음 **추가** 단추를 선택 합니다.

1. 다음 코드를 복사하여 편집기에서 *annotations.cpp* 파일에 붙여넣습니다.

    ```cpp
    #include "annotations.h"
    #include <malloc.h>

    _Ret_maybenull_ LinkedList* AllocateNode()
    {
        LinkedList* result = static_cast<LinkedList*>(malloc(sizeof(LinkedList)));
        return result;
    }

    LinkedList* AddTail(LinkedList* node, int value)
    {
        // finds the last node
        while (node->next != nullptr)
        {
            node = node->next;
        }

        // appends the new node
        LinkedList* newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }
    ```

1. 메뉴 모음에서 **파일**  >  **모두 저장** 을 선택 합니다.

이제 솔루션이 완성되고 오류 없이 빌드됩니다.

::: moniker range="msvc-150"

> [!NOTE]
> Visual Studio 2017에서는 IntelliSense 엔진에 의사 경고가 표시 될 수 있습니다 `E1097 unknown attribute "no_init_all"` . 이 경고는 무시해도 됩니다.

::: moniker-end
