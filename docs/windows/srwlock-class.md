---
title: SRWLock 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs:
- C++
helpviewer_keywords:
- SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fb97a29796c287cfaadddc305f25807de5dcba2e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604238"
---
# <a name="srwlock-class"></a>SRWLock 클래스

슬림 판독기/작성기 잠금을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class SRWLock;
```

## <a name="remarks"></a>설명

슬림 판독기/기록기 잠금 개체 또는 리소스에는 스레드 간에 액세스를 동기화에 사용 됩니다. 자세한 내용은 [동기화 함수](/windows/desktop/Sync/synchronization-functions)합니다.

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|||
|-|-|
|`SyncLockExclusive`|동의어는 **SRWLock** 배타 모드에 획득 된 개체입니다.|
|`SyncLockShared`|동의어는 **SRWLock** 공유 모드에서 획득 된 개체입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[SRWLock::SRWLock 생성자](../windows/srwlock-srwlock-constructor.md)|새 인스턴스를 초기화 합니다 **SRWLock** 클래스입니다.|
|[SRWLock::~SRWLock 소멸자](../windows/srwlock-tilde-srwlock-destructor.md)|인스턴스를 초기화 해제 합니다 **SRWLock** 클래스입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[SRWLock::LockExclusive 메서드](../windows/srwlock-lockexclusive-method.md)|획득 한 **SRWLock** 단독 모드의 개체입니다.|
|[SRWLock::LockShared 메서드](../windows/srwlock-lockshared-method.md)|획득 한 **SRWLock** 공유 모드의 개체입니다.|
|[SRWLock::TryLockExclusive 메서드](../windows/srwlock-trylockexclusive-method.md)|획득 하 려는 **SRWLock** 개체의 현재 또는 지정 된 단독 모드 **SRWLock** 개체입니다.|
|[SRWLock::TryLockShared 메서드](../windows/srwlock-trylockshared-method.md)|획득 하 려는 **SRWLock** 개체를 현재 또는 지정 된 공유 모드로 **SRWLock** 개체입니다.|

### <a name="protected-data-member"></a>보호 된 데이터 멤버

|name|설명|
|----------|-----------------|
|[SRWLock::SRWLock_ 데이터 멤버](../windows/srwlock-srwlock-data-member.md)|현재 기본 잠금 변수를 포함 **SRWLock** 개체입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층

`SRWLock`

## <a name="requirements"></a>요구 사항

**헤더:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>참고 항목

[Microsoft::WRL::Wrappers 네임스페이스](../windows/microsoft-wrl-wrappers-namespace.md)