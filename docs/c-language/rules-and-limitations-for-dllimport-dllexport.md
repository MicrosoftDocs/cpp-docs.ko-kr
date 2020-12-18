---
description: '자세한 정보: dllimport/dllexport에 대한 규칙 및 제한'
title: dllimport-dllexport에 대한 규칙 및 제한
ms.date: 11/04/2016
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
ms.openlocfilehash: 6d7de92b7d58eacc9334859a865e0e1456fffcb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292886"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>dllimport/dllexport에 대한 규칙 및 제한

**Microsoft 전용**

- **`dllimport`** 또는 `dllexport` 특성을 포함하지 않고 선언하는 함수는 DLL 인터페이스의 일부분으로 간주되지 않습니다. 따라서 해당 모듈 또는 같은 프로그램의 다른 모듈에 함수 정의가 있어야 합니다. 함수를 DLL 인터페이스에 포함하려면 다른 모듈에서 함수의 정의를 `dllexport`로 선언해야 합니다. 그러지 않으면 클라이언트를 빌드할 때 링커 오류가 발생합니다.

- 프로그램의 모듈 하나에 동일 함수에 대한 **`dllimport`** 및 `dllexport` 선언이 포함되어 있으면 `dllexport` 특성이 **`dllimport`** 특성보다 우선적으로 사용됩니다. 그러나 이 경우 컴파일러 경고가 생성됩니다. 예를 들어:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllExport void func1( void );   /* Warning; dllexport */
                                       /* takes precedence. */

    ```

- **`dllimport`** 특성을 사용하여 선언된 데이터 개체의 주소로 정적 데이터 포인터를 초기화할 수는 없습니다. 예를 들어, 다음 코드는 오류를 생성합니다.

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport int i;
       .
       .
       .
       int *pi = &i;                           /* Error */

       void func2()
       {
          static int *pi = &i;                   /* Error */
       }

    ```

- **`dllimport`** 를 사용하여 선언된 함수의 주소로 정적 함수 포인터를 초기화하면 해당 포인터는 함수의 주소가 아닌 DLL 가져오기 썽크(컨트롤을 함수로 전송하는 코드 스텁)의 주소로 설정됩니다. 이 할당에서는 오류 메시지가 생성되지 않습니다.

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void
       .
       .
       .
       static void ( *pf )( void ) = &func1;   /* No Error */

       void func2()
       {
          static void ( *pf )( void ) = &func1;  /* No Error */
       }

    ```

- 개체 선언에 `dllexport` 특성을 포함하는 프로그램은 해당 개체의 정의를 제공해야 하므로 `dllexport` 함수의 주소로 전역 또는 로컬 정적 함수 포인터를 초기화할 수 있습니다. 마찬가지로 `dllexport` 데이터 개체의 주소로 전역 또는 로컬 정적 데이터 포인터를 초기화할 수 있습니다. 예를 들어:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllImport int i;

       DllExport void func1( void );
       DllExport int i;
       .
       .
       .
       int *pi = &i;                            /* Okay */
       static void ( *pf )( void ) = &func1;    /* Okay */

       void func2()
       {
          static int *pi = i;                     /* Okay */
          static void ( *pf )( void ) = &func1;   /* Okay */
       }

    ```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[DLL 가져오기 및 내보내기 함수](../c-language/dll-import-and-export-functions.md)
