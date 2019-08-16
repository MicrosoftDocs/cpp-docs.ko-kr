---
title: uuid(C++ 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: d644f59ac92bf4e39f191c291dd4fef626411c3d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514943"
---
# <a name="uuid-c-attributes"></a>uuid(C++ 특성)

클래스 또는 인터페이스의 고유 ID를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>매개 변수

*uuid*<br/>
128 비트 고유 식별자입니다.

## <a name="remarks"></a>설명

인터페이스 또는 클래스의 정의에서 **uuid** C++ 특성을 지정 하지 않는 경우 Microsoft C++ 컴파일러에서이를 제공 합니다. **Uuid**를 지정 하는 경우 따옴표를 포함 해야 합니다.

**Uuid**를 지정 하지 않으면 컴파일러는 컴퓨터의 다른 특성 프로젝트에서 이름이 같은 인터페이스 또는 클래스에 대해 동일한 GUID를 생성 합니다.

Uuidgen.exe 또는 Guidgen.exe를 사용 하 여 고유한 Id를 생성할 수 있습니다. 이러한 도구 중 하나를 실행 하려면 **시작** 을 클릭 하 고 메뉴에서 **실행** 을 클릭 합니다. 그런 다음 필요한 도구의 이름을 입력 합니다.

ATL을 사용 하지 않는 프로젝트에서 사용 하는 경우 uuid 특성을 지정 하는 것은 [uuid](../../cpp/uuid-cpp.md) **__declspec** 한정자를 지정 하는 것과 같습니다. [__Uuidof](../../cpp/uuidof-operator.md) 를 사용 하 여 클래스의 **uuid** 를 검색할 수 있습니다.

## <a name="example"></a>예제

**Uuid**의 샘플 사용에 대 한 [바인딩](bindable.md) 가능한 예제를 참조 하십시오.

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|**클래스**, **구조체**, **인터페이스**, **공용 구조체**, **열거형**|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고자료

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)