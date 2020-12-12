---
description: '자세한 정보: Platform:: Metadata 네임 스페이스'
title: Platform::Metadata 네임스페이스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata
helpviewer_keywords:
- Platform::Metadata Namespace
ms.assetid: e3e114d8-a4b0-47f0-865a-9ce9d7212e86
ms.openlocfilehash: 5dd699c0136c4ee37462dd22f9ee27bec345e8b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308395"
---
# <a name="platformmetadata-namespace"></a>Platform::Metadata 네임스페이스

이 네임스페이스는 형식 선언을 수정하는 특성을 포함합니다.

## <a name="syntax"></a>구문

```cpp
namespace Platform {
   namespace Metadata {
}}
```

### <a name="members"></a>멤버

이 네임스페이스는 내부용으로 설계되었지만 브라우저에서 이 네임스페이스의 다음 멤버를 표시할 수 있습니다.

|Name|설명|
|----------|------------|
|특성|특성의 기본 클래스입니다.|
|[Platform:: Metadata::D efaultMemberAttribute 특성](../cppcx/platform-metadata-defaultmemberattribute-attribute.md)|몇 가지 가능한 오버로드된 함수 중에서 호출할 기본 설정 함수를 나타냅니다.|
|[Platform::Metadata::FlagsAttribute Attribute](../cppcx/platform-metadata-flagsattribute-attribute.md)Flags|열거형을 비트 필드의 열거형으로 선언합니다.<br /><br /> 다음 예제에서는 열거형에 `Flags` 특성을 적용하는 방법을 보여 줍니다.<br /><br /> `[Flags] enum class MyEnumeration { enumA = 1, enumB = 2, enumC = 3}`|
|[Platform::Metadata::RuntimeClassNameAttribute](../cppcx/platform-metadata-runtimeclassname.md)|private ref 클래스에 유효한 런타임 클래스 이름이 있는지 확인합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`Platform`

### <a name="requirements"></a>요구 사항

**메타 데이터:** platform.object

**네임스페이스:** Platform::Metadata

## <a name="see-also"></a>참고 항목

[Platform 네임 스페이스](platform-namespace-c-cx.md)
