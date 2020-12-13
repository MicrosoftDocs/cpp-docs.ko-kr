---
description: '자세한 정보: CMutex 클래스'
title: CMutex 클래스
ms.date: 11/04/2016
f1_keywords:
- CMutex
- AFXMT/CMutex
- AFXMT/CMutex::CMutex
helpviewer_keywords:
- CMutex [MFC], CMutex
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
ms.openlocfilehash: 4890a99d52fb8142bac0cc25d6a23ef6dbcaed5b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331492"
---
# <a name="cmutex-class"></a>CMutex 클래스

한 스레드가 리소스에 상호 배타적으로 액세스할 수 있도록 하는 동기화 개체인 "뮤텍스"를 나타냅니다.

## <a name="syntax"></a>구문

```
class CMutex : public CSyncObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMutex:: CMutex](#cmutex)|`CMutex` 개체를 생성합니다.|

## <a name="remarks"></a>설명

뮤텍스는 한 번에 하나의 스레드만 데이터 또는 다른 제어 된 리소스를 수정할 수 있는 경우에 유용 합니다. 예를 들어 연결 된 목록에 노드를 추가 하는 프로세스는 한 번에 하나의 스레드에서만 허용 해야 하는 프로세스입니다. 개체를 사용 하 여 `CMutex` 연결 된 목록을 제어 하면 한 번에 하나의 스레드만 목록에 액세스할 수 있습니다.

개체를 사용 하려면 `CMutex` `CMutex` 필요한 경우 개체를 구성 합니다. 대기 하려는 뮤텍스의 이름을 지정 하 고 응용 프로그램에서 초기에 해당 뮤텍스를 소유 해야 합니다. 그런 다음 생성자가를 반환할 때 뮤텍스에 액세스할 수 있습니다. 제어 되는 리소스에 대 한 액세스가 완료 되 면 [CSyncObject:: Unlock](../../mfc/reference/csyncobject-class.md#unlock) 을 호출 합니다.

개체를 사용 하는 다른 방법은 `CMutex` 제어 하려는 클래스에 형식의 변수를 데이터 멤버로 추가 하는 것입니다 `CMutex` . 제어 되는 개체를 생성 하는 동안 `CMutex` 뮤텍스를 처음 소유 하 고 있는지, 뮤텍스 이름 (프로세스 경계에서 사용 되는 경우) 및 필요한 보안 특성을 지정 하는 데이터 멤버의 생성자를 호출 합니다.

이러한 방식으로 개체에 의해 제어 되는 리소스에 액세스 하려면 `CMutex` 먼저 리소스의 액세스 멤버 함수에 [Csinglelock](../../mfc/reference/csinglelock-class.md) 형식의 변수 또는 [CMultiLock](../../mfc/reference/cmultilock-class.md) 형식을 만듭니다. 그런 다음, lock 개체의 `Lock` 멤버 함수 (예 [: Csinglelock:: lock](../../mfc/reference/csinglelock-class.md#lock))를 호출 합니다. 이 시점에서 스레드는 리소스에 대 한 액세스 권한을 획득 하 고 리소스를 해제 하 고 액세스할 때까지 기다리거나 리소스가 해제 되 고 시간이 초과 될 때까지 대기 하 여 리소스에 대 한 액세스 권한을 얻을 수 없습니다. 어떤 경우 든 리소스는 스레드로부터 안전한 방식으로 액세스 됩니다. 리소스를 해제 하려면 lock 개체의 `Unlock` 멤버 함수 (예: [csinglelock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock))를 사용 하거나 lock 개체가 범위를 벗어나는 것을 허용 합니다.

개체를 사용 하는 방법에 대 한 자세한 내용은 `CMutex` [다중 스레딩: 동기화 클래스 사용 방법](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CMutex`

## <a name="requirements"></a>요구 사항

**헤더:** afxmt

## <a name="cmutexcmutex"></a><a name="cmutex"></a> CMutex:: CMutex

명명 되거나 명명 되지 않은 `CMutex` 개체를 생성 합니다.

```
CMutex(
    BOOL bInitiallyOwn = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>매개 변수

*bInitiallyOwn*<br/>
개체를 만드는 스레드에서 처음에 `CMutex` 뮤텍스를 통해 제어 되는 리소스에 액세스할 수 있는지 여부를 지정 합니다.

*lpszName*<br/>
`CMutex` 개체의 이름입니다. 동일한 이름을 가진 다른 뮤텍스가 있는 경우 해당 개체가 프로세스 경계를 넘어 사용 될 경우 *lpszName* 을 제공 해야 합니다. **NULL** 인 경우 뮤텍스의 이름이 지정 되지 않습니다. 이름이 기존 뮤텍스와 일치 하는 경우 생성자는 `CMutex` 해당 이름의 뮤텍스를 참조 하는 새 개체를 빌드합니다. 이름이 뮤텍스가 아닌 기존 동기화 개체와 일치 하는 경우 생성이 실패 합니다.

*lpsaAttribute*<br/>
뮤텍스 개체의 보안 특성입니다. 이 구조에 대 한 자세한 내용은 Windows SDK [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 을 참조 하십시오.

### <a name="remarks"></a>설명

개체를 액세스 하거나 해제 하려면 `CMutex` [CMultiLock](../../mfc/reference/cmultilock-class.md) 또는 [csinglelock](../../mfc/reference/csinglelock-class.md) 개체를 만들고 해당 [잠금](../../mfc/reference/csinglelock-class.md#lock) 및 잠금 [해제](../../mfc/reference/csinglelock-class.md#unlock) 멤버 함수를 호출 합니다. `CMutex`개체가 독립 실행형으로 사용 되는 경우 해당 멤버 함수를 호출 하 여 해당 개체를 `Unlock` 해제 합니다.

> [!IMPORTANT]
> 개체를 만든 후 `CMutex` 에는 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 사용 하 여 뮤텍스가 아직 존재 하지 않는지 확인 합니다. 뮤텍스가 예기치 않게 존재 하는 경우 rogue 프로세스가 squatting을 나타낼 수 있으며 뮤텍스를 악의적으로 사용 하려고 할 수 있습니다. 이 경우에 권장 되는 보안 인식 절차는 핸들을 닫고 개체를 만드는 동안 오류가 발생 한 것 처럼 계속 진행 하는 것입니다.

## <a name="see-also"></a>참고 항목

[CSyncObject 클래스](../../mfc/reference/csyncobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
