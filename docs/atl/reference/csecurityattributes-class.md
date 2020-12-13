---
description: '자세히 알아보기: CSecurityAttributes 클래스'
title: CSecurityAttributes 클래스
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: 8cb772e574aef4ad941feef1cb838fb91d937576
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140818"
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes 클래스

이 클래스는 보안 특성 구조에 대 한 씬 래퍼입니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSecurityAttributes:: CSecurityAttributes](#csecurityattributes)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSecurityAttributes:: Set](#set)|개체의 특성을 설정 하려면이 메서드를 호출 `CSecurityAttributes` 합니다.|

## <a name="remarks"></a>설명

구조체에는 `SECURITY_ATTRIBUTES` 개체를 만드는 데 사용 되는 [보안 설명자](/windows/win32/api/winnt/ns-winnt-security_descriptor) 가 포함 되어 있으며이 구조를 지정 하 여 검색 된 핸들이 상속 가능한 지 여부를 지정 합니다.

Windows의 액세스 제어 모델에 대 한 소개는 Windows SDK [Access Control](/windows/win32/SecAuthZ/access-control) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="csecurityattributescsecurityattributes"></a><a name="csecurityattributes"></a> CSecurityAttributes:: CSecurityAttributes

생성자입니다.

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>매개 변수

*rSecurityDescriptor*<br/>
보안 설명자에 대한 참조입니다.

*bInheritsHandle*<br/>
새 프로세스가 만들어질 때 반환된 핸들의 상속 여부를 지정합니다. 이 멤버가 true이면 새 프로세스가 핸들을 상속합니다.

## <a name="csecurityattributesset"></a><a name="set"></a> CSecurityAttributes:: Set

개체의 특성을 설정 하려면이 메서드를 호출 `CSecurityAttributes` 합니다.

```cpp
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>매개 변수

*rSecurityDescriptor*<br/>
보안 설명자에 대한 참조입니다.

*bInheritHandle*<br/>
새 프로세스가 만들어질 때 반환된 핸들의 상속 여부를 지정합니다. 이 멤버가 true이면 새 프로세스가 핸들을 상속합니다.

### <a name="remarks"></a>설명

이 메서드는 생성자에서 개체를 초기화 하는 데 사용 됩니다 `CSecurityAttributes` .

## <a name="see-also"></a>참고 항목

[보안 샘플](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[보안 설명자](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[보안 전역 함수](../../atl/reference/security-global-functions.md)
