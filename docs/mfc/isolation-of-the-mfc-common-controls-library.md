---
description: '자세히 알아보기: MFC 공용 컨트롤 라이브러리 격리'
title: MFC 공용 컨트롤 라이브러리 격리
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, Common Controls library
ms.assetid: 7471e6f0-49b0-47f7-86e7-8d6bc3541694
ms.openlocfilehash: f3e0f6ad981a690f6212455b8af891eaa97f2642
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335818"
---
# <a name="isolation-of-the-mfc-common-controls-library"></a>MFC 공용 컨트롤 라이브러리 격리

공용 컨트롤 라이브러리는 이제 MFC 내에서 격리 되므로 다른 모듈 (예: 사용자 Dll)이 매니페스트에 버전을 지정 하 여 다른 버전의 공용 컨트롤 라이브러리를 사용할 수 있습니다.

MFC 응용 프로그램 (또는 MFC에서 호출 하는 사용자 코드)은 FunctionName 이라는 래퍼 함수를 통해 공용 컨트롤 라이브러리 Api를 호출 `Afx` 합니다. 여기서 *FUNCTIONNAME* 는 공용 컨트롤 API의 이름입니다. 이러한 래퍼 함수는 afxcomctl32.h 및 afxcomctl32.h에 정의 되어 있습니다.

[AFX_COMCTL32_IF_EXISTS](reference/run-time-object-model-services.md#afx_comctl32_if_exists) 및 [AFX_COMCTL32_IF_EXISTS2](reference/run-time-object-model-services.md#afx_comctl32_if_exists2) 매크로 (afxcomctl32.h에 정의 됨)를 사용 하 여 공용 컨트롤 라이브러리가 [GetProcAddress](../build/getprocaddress.md)를 호출 하는 대신 특정 API를 구현 하는지 여부를 결정할 수 있습니다.

기술적으로 래퍼 클래스 `CComCtlWrapper` (afxcomctl32.h에 정의 됨)를 통해 공용 컨트롤 라이브러리 api에 대 한 호출을 수행 합니다. `CComCtlWrapper` 는 comctl32.dll 로드 및 언로드를 담당 하기도 합니다. MFC 모듈 상태에는의 인스턴스에 대 한 포인터가 포함 되어 있습니다 `CComCtlWrapper` . 매크로를 사용 하 여 래퍼 클래스에 액세스할 수 있습니다 `afxComCtlWrapper` .

Mfc 응용 프로그램 또는 사용자 dll을 mfc 응용 프로그램 또는 사용자 DLL에서 직접 호출 하는 경우에는 mfc 래퍼 함수를 사용 하지 않고 공용 컨트롤 API를 직접 호출 하는 것은 대부분의 경우에 작동 합니다. MFC 응용 프로그램 또는 사용자 DLL은 해당 매니페스트에서 요청한 공용 컨트롤 라이브러리에 바인딩되어 있기 때문입니다. 그러나 다른 공용 컨트롤 라이브러리 버전을 사용 하는 사용자 Dll에서 MFC 코드를 호출할 수 있으므로 MFC 코드 자체는 래퍼를 사용 해야 합니다.
