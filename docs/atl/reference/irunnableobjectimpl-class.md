---
description: '자세히 알아보기: IRunnableObjectImpl 클래스'
title: IRunnableObjectImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
ms.openlocfilehash: ecae31d23eb68ce45e9b140a3e5034fb6c5400fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158116"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl 클래스

이 클래스는 `IUnknown` 를 구현 하 고 [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) 인터페이스의 기본 구현을 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 클래스 `IRunnableObjectImpl` 입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|실행 중인 컨트롤의 CLSID를 반환 합니다. ATL 구현은 GUID_NULL로 CLSID를 설정 하 고 E_UNEXPECTED를 반환 합니다.|
|[IRunnableObjectImpl:: IsRunning](#isrunning)|컨트롤이 실행 중인지 여부를 확인 합니다. ATL 구현에서 TRUE를 반환 합니다.|
|[IRunnableObjectImpl:: LockRunning](#lockrunning)|컨트롤을 실행 상태로 잠급니다. ATL 구현은 S_OK 반환 합니다.|
|[IRunnableObjectImpl:: Run](#run)|컨트롤을 강제로 실행 합니다. ATL 구현은 S_OK 반환 합니다.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|컨트롤이 포함 되어 있음을 나타냅니다. ATL 구현은 S_OK 반환 합니다.|

## <a name="remarks"></a>설명

[IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject) 인터페이스를 사용 하면 컨테이너에서 컨트롤이 실행 중인지 여부를 확인 하 고 실행 하거나 실행 상태로 잠글 수 있습니다. 클래스는 `IRunnableObjectImpl` 이 인터페이스의 기본 구현을 제공 하 고 `IUnknown` 디버그 빌드에서 정보를 덤프 장치로 전송 하 여를 구현 합니다.

**관련 문서** [ATL 자습서](../../atl/active-template-library-atl-tutorial.md), [atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="irunnableobjectimplgetrunningclass"></a><a name="getrunningclass"></a> IRunnableObjectImpl::GetRunningClass

실행 중인 컨트롤의 CLSID를 반환 합니다.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>반환 값

ATL 구현은 \* *lpclsid* 를 GUID_NULL 설정 하 고 E_UNEXPECTED를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IRunnableObject:: GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) 를 참조 하세요.

## <a name="irunnableobjectimplisrunning"></a><a name="isrunning"></a> IRunnableObjectImpl:: IsRunning

컨트롤이 실행 중인지 여부를 확인 합니다.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>반환 값

ATL 구현에서 TRUE를 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IRunnableObject:: IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) 을 참조 하세요.

## <a name="irunnableobjectimpllockrunning"></a><a name="lockrunning"></a> IRunnableObjectImpl:: LockRunning

컨트롤을 실행 상태로 잠급니다.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>반환 값

ATL 구현은 S_OK 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [실행 되는 IRunnableObject:: lockrunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) 을 참조 하세요.

## <a name="irunnableobjectimplrun"></a><a name="run"></a> IRunnableObjectImpl:: Run

컨트롤을 강제로 실행 합니다.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>반환 값

ATL 구현은 S_OK 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IRunnableObject:: Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) 을 참조 하십시오.

## <a name="irunnableobjectimplsetcontainedobject"></a><a name="setcontainedobject"></a> IRunnableObjectImpl::SetContainedObject

컨트롤이 포함 되어 있음을 나타냅니다.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>반환 값

ATL 구현은 S_OK 반환 합니다.

### <a name="remarks"></a>설명

Windows SDK에서 [IRunnableObject:: SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CComControl 클래스](../../atl/reference/ccomcontrol-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
