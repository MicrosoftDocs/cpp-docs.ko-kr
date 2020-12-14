---
description: '자세한 정보: 내보낸 DLL 함수 진입점'
title: 내보낸 DLL 함수 시작 지점
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [MFC], functions
- MFC, managing state data
- state management [MFC], exported DLLs
ms.assetid: 3268666e-d24b-44f2-80e8-7c80f73b93ca
ms.openlocfilehash: ea30a36507e22beed1f36727b8e7b582d51929b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314596"
---
# <a name="exported-dll-function-entry-points"></a>내보낸 DLL 함수 시작 지점

DLL의 내보낸 함수에 대 한 [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) 매크로를 사용 하 여 dll 모듈에서 호출 하는 응용 프로그램의 dll로 전환할 때 적절 한 전역 상태를 유지 관리 합니다.

이 매크로는 호출 될 때 `pModuleState` 모듈의 전역 데이터를 포함 하는 구조체에 대 한 포인터를 포함 하는 `AFX_MODULE_STATE` 함수의 나머지 범위에 대 한 유효한 모듈 상태로 설정 됩니다. 매크로가 포함 된 범위를 벗어나면 이전의 유효 모듈 상태가 자동으로 복원 됩니다.

이러한 전환은 스택에서 클래스의 인스턴스를 생성 하 여 이루어집니다 `AFX_MODULE_STATE` . 이 클래스는 생성자에서 현재 모듈 상태에 대 한 포인터를 가져와 멤버 변수에 저장 한 다음를 `pModuleState` 새로운 유효 모듈 상태로 설정 합니다. 소멸자에서이 클래스는 해당 멤버 변수에 저장 된 포인터를 유효한 모듈 상태로 복원 합니다.

DLL에서 대화 상자를 시작 하는 함수가 있는 경우 함수 시작 부분에 다음 코드를 추가 해야 합니다.

[!code-cpp[NVC_MFCConnectionPoints#6](codesnippet/cpp/exported-dll-function-entry-points_1.cpp)]

현재 범위 끝까지 [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) 에서 반환 된 상태로 현재 모듈 상태를 바꿉니다.

매크로를 사용 하지 않는 경우 Dll의 리소스 문제는 발생 `AFX_MANAGE_STATE` 합니다. 기본적으로 MFC는 주 응용 프로그램의 리소스 핸들을 사용 하 여 리소스 템플릿을 로드 합니다. 이 템플릿은 실제로 DLL에 저장 됩니다. 근본 원인은 MFC의 모듈 상태 정보가 매크로로 전환 되지 않았기 때문입니다 `AFX_MANAGE_STATE` . 리소스 핸들은 MFC의 모듈 상태에서 복구 됩니다. 모듈 상태를 전환 하지 않으면 잘못 된 리소스 핸들이 사용 됩니다.

`AFX_MANAGE_STATE` 는 DLL의 모든 함수에 넣을 필요가 없습니다. 예를 들어,를 사용 하 여 `InitInstance` 응용 프로그램의 mfc 코드에서를 호출할 수 있습니다 `AFX_MANAGE_STATE` `InitInstance` `InitInstance` . 모든 메시지 매핑 처리기의 경우에도 마찬가지입니다. 일반 MFC Dll은 메시지를 라우팅하기 전에 모듈 상태를 자동으로 전환 하는 특수 한 마스터 창 프로시저를 포함 합니다.

## <a name="see-also"></a>참고 항목

[MFC 모듈의 상태 데이터 관리](managing-the-state-data-of-mfc-modules.md)
