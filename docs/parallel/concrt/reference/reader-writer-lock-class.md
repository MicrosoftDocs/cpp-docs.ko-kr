---
description: Reader_writer_lock 클래스에 대해 자세히 알아보세요.
title: reader_writer_lock 클래스
ms.date: 11/04/2016
f1_keywords:
- reader_writer_lock
- CONCRT/concurrency::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock
- CONCRT/concurrency::reader_writer_lock::scoped_lock_read
- CONCRT/concurrency::reader_writer_lock::reader_writer_lock
- CONCRT/concurrency::reader_writer_lock::lock
- CONCRT/concurrency::reader_writer_lock::lock_read
- CONCRT/concurrency::reader_writer_lock::try_lock
- CONCRT/concurrency::reader_writer_lock::try_lock_read
- CONCRT/concurrency::reader_writer_lock::unlock
helpviewer_keywords:
- reader_writer_lock class
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
ms.openlocfilehash: 68f42fbce607f05ceb489967d2b13cd08068d0cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115224"
---
# <a name="reader_writer_lock-class"></a>reader_writer_lock 클래스

로컬 전용 회전을 사용한 작성기 우선 큐 기반 읽기/쓰기 잠금입니다. 잠금은 작성기에 대해 FIFO(선입 선출) 액세스 권한을 부여하며 작성기의 연속 부하 상태에서는 판독기에 제공되지 않습니다.

## <a name="syntax"></a>구문

```cpp
class reader_writer_lock;
```

## <a name="members"></a>멤버

### <a name="public-classes"></a>public 클래스

|Name|설명|
|----------|-----------------|
|[reader_writer_lock::scoped_lock 클래스](#scoped_lock_class)|잠금 개체를 작성기로 가져오는 데 사용할 수 있는 예외 안전 RAII 래퍼입니다 `reader_writer_lock` .|
|[reader_writer_lock::scoped_lock_read 클래스](#scoped_lock_read_class)|잠금 개체를 판독기로 가져오는 데 사용할 수 있는 예외 안전 RAII 래퍼입니다 `reader_writer_lock` .|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[reader_writer_lock](#ctor)|새 `reader_writer_lock` 개체를 생성합니다.|
|[~ reader_writer_lock 소멸자](#dtor)|개체를 소멸 시킵니다 `reader_writer_lock` .|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[lock](#lock)|작성기로 판독기-작성기 잠금을 가져옵니다.|
|[lock_read](#lock_read)|판독기로 판독기-작성기 잠금을 가져옵니다. 작성기가 있는 경우 활성 판독기는 완료 될 때까지 기다려야 합니다. 판독기는 단순히 잠금에 관심을 등록 하 고 작성기가 잠금을 해제 하기를 기다립니다.|
|[try_lock](#try_lock)|판독기-작성기 잠금을 차단 하지 않고 작성기로 가져오려고 시도 합니다.|
|[try_lock_read](#try_lock_read)|판독기에서 판독기로 잠금을 차단 하지 않고 가져오려고 시도 합니다.|
|[잠금을](#unlock)|판독기 또는 작성자를 잠근 사용자를 기준으로 판독기 작성기 잠금을 해제 합니다.|

## <a name="remarks"></a>설명

자세한 내용은 [동기화 데이터 구조](../../../parallel/concrt/synchronization-data-structures.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`reader_writer_lock`

## <a name="requirements"></a>요구 사항

**헤더:** concrt .h

**네임 스페이스:** 동시성

## <a name="lock"></a><a name="lock"></a> 잠기지

작성기로 판독기-작성기 잠금을 가져옵니다.

```cpp
void lock();
```

### <a name="remarks"></a>설명

[Scoped_lock](#scoped_lock_class) 구문을 사용 하 여 예외 안전 방식으로 개체를 작성기로 얻고 해제 하는 것이 더 안전 `reader_writer_lock` 합니다.

작성기가 잠금을 가져오려고 시도하면 이후 판독기는 작성기가 잠금을 성공적으로 가져와 해제할 때까지 차단됩니다. 이 잠금은 작성기에 적용 되며 작성자의 연속 로드에서 판독기를 결핍 수 있습니다.

작성기는 잠금을 해제 하 여 잠금을 종료 하면 다음 기록기가 줄에서 해제 되도록 연결 됩니다.

호출 컨텍스트에서 잠금이 이미 유지 되 고 있으면 [improper_lock](improper-lock-class.md) 예외가 throw 됩니다.

## <a name="lock_read"></a><a name="lock_read"></a> lock_read

판독기로 판독기-작성기 잠금을 가져옵니다. 작성기가 있는 경우 활성 판독기는 완료 될 때까지 기다려야 합니다. 판독기는 단순히 잠금에 관심을 등록 하 고 작성기가 잠금을 해제 하기를 기다립니다.

```cpp
void lock_read();
```

### <a name="remarks"></a>설명

[Scoped_lock_read](#scoped_lock_read_class) 구문을 사용 하 여 예외 안전 방식으로 개체를 판독기로 얻고 해제 하는 것이 더 안전 `reader_writer_lock` 합니다.

잠금을 기다리는 작성기가 있는 경우 판독기는 줄의 모든 작성기가 잠금을 획득 하 고 해제할 때까지 기다립니다. 이 잠금은 작성기에 적용 되며 작성자의 연속 로드에서 판독기를 결핍 수 있습니다.

## <a name="reader_writer_lock"></a><a name="ctor"></a> reader_writer_lock

새 `reader_writer_lock` 개체를 생성합니다.

```cpp
reader_writer_lock();
```

## <a name="reader_writer_lock"></a><a name="dtor"></a> ~ reader_writer_lock

개체를 소멸 시킵니다 `reader_writer_lock` .

```cpp
~reader_writer_lock();
```

### <a name="remarks"></a>설명

소멸자가 실행 될 때 잠금이 더 이상 유지 되지 않을 것으로 예상 됩니다. 판독기 작성기 잠금이 잠금으로 소멸 되도록 허용 하면 정의 되지 않은 동작이 발생 합니다.

## <a name="reader_writer_lockscoped_lock-class"></a><a name="scoped_lock_class"></a> reader_writer_lock:: scoped_lock 클래스

잠금 개체를 작성기로 가져오는 데 사용할 수 있는 예외 안전 RAII 래퍼입니다 `reader_writer_lock` .

```cpp
class scoped_lock;
```

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_ctor"></a> scoped_lock:: scoped_lock

개체를 생성 `scoped_lock` 하 고 `reader_writer_lock` `_Reader_writer_lock` 매개 변수에서 작성기로 전달 된 개체를 가져옵니다. 다른 스레드에서 잠금을 보유 하 고 있으면이 호출은 차단 됩니다.

```cpp
explicit _CRTIMP scoped_lock(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>매개 변수

*_Reader_writer_lock*<br/>
`reader_writer_lock`작성기로 가져올 개체입니다.

## <a name="scoped_lockscoped_lock"></a><a name="scoped_lock_dtor"></a> scoped_lock:: ~ scoped_lock

개체를 소멸 시키고 `reader_writer_lock` 해당 생성자에 제공 된 잠금을 해제 합니다.

```cpp
~scoped_lock();
```

## <a name="reader_writer_lockscoped_lock_read-class"></a><a name="scoped_lock_read_class"></a> reader_writer_lock:: scoped_lock_read 클래스

잠금 개체를 판독기로 가져오는 데 사용할 수 있는 예외 안전 RAII 래퍼입니다 `reader_writer_lock` .

```cpp
class scoped_lock_read;
```

## <a name="scoped_lock_readscoped_lock_read"></a><a name="scoped_lock_read_ctor"></a> scoped_lock_read:: scoped_lock_read

개체를 생성 `scoped_lock_read` 하 고 `reader_writer_lock` `_Reader_writer_lock` 판독기로 매개 변수에 전달 된 개체를 가져옵니다. 다른 스레드에서 잠금을 작성기로 보유 하거나 보류 중인 작성자가 있는 경우이 호출은 차단 됩니다.

```cpp
explicit _CRTIMP scoped_lock_read(reader_writer_lock& _Reader_writer_lock);
```

### <a name="parameters"></a>매개 변수

*_Reader_writer_lock*<br/>
`reader_writer_lock`판독기로 가져올 개체입니다.

## <a name="a-namescoped_lock_read_dtor--reader_writer_lockscoped_lock_readscoped_lock_read-destructor"></a><a name="scoped_lock_read_dtor">  reader_writer_lock:: scoped_lock_read:: ~ scoped_lock_read 소멸자

개체를 소멸 시키고 `scoped_lock_read` 해당 생성자에 제공 된 잠금을 해제 합니다.

```cpp
~scoped_lock_read();
```

## <a name="try_lock"></a><a name="try_lock"></a> try_lock

판독기-작성기 잠금을 차단 하지 않고 작성기로 가져오려고 시도 합니다.

### <a name="syntax"></a>구문

```cpp
bool try_lock();
```

### <a name="return-value"></a>Return Value

잠금을 획득 한 경우 값 **`true`** 이 고, 그렇지 않으면 값 **`false`** 입니다.

## <a name="try_lock_read"></a><a name="try_lock_read"></a> try_lock_read

판독기에서 판독기로 잠금을 차단 하지 않고 가져오려고 시도 합니다.

```cpp
bool try_lock_read();
```

### <a name="return-value"></a>반환 값

잠금을 획득 한 경우 값 **`true`** 이 고, 그렇지 않으면 값 **`false`** 입니다.

## <a name="unlock"></a><a name="unlock"></a> 잠금을

판독기 또는 작성자를 잠근 사용자를 기준으로 판독기 작성기 잠금을 해제 합니다.

```cpp
void unlock();
```

### <a name="remarks"></a>설명

잠금을 기다리는 작성기가 있는 경우 잠금 해제는 항상 FIFO 순서에서 다음 기록기로 이동 합니다. 이 잠금은 작성기에 적용 되며 작성자의 연속 로드에서 판독기를 결핍 수 있습니다.

## <a name="see-also"></a>참고 항목

[concurrency 네임 스페이스](concurrency-namespace.md)<br/>
[critical_section 클래스](critical-section-class.md)
