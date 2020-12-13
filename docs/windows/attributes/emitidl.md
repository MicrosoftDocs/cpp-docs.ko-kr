---
description: '자세히 알아보기: emitidl'
title: emitidl (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.emitidl
helpviewer_keywords:
- emitidl attribute
ms.assetid: 85b80c56-578e-4392-ac03-8443c74ebb7d
ms.openlocfilehash: 21c4f7fc067eb37b8816bdedd1f338908950566e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337801"
---
# <a name="emitidl"></a>emitidl

모든 후속 IDL 특성을 처리 하 고 생성 된 .idl 파일에 배치할지 여부를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ emitidl(state, defaultimports=boolean) ];
```

### <a name="parameters"></a>매개 변수

*state*<br/>
이러한 가능한 값 중 하나는 **`true`** , **`false`** , `forced` , `restricted` , `push` 또는 `pop` 입니다.

- 인 경우 **`true`** 소스 코드 파일에서 발생 하는 모든 idl 범주 특성이 생성 된 .idl 파일에 배치 됩니다. **Emitidl** 에 대 한 기본 설정입니다.

- 인 경우 **`false`** 소스 코드 파일에서 발생 하는 모든 idl 범주 특성은 생성 된 .idl 파일에 배치 되지 않습니다.

- 인 경우 `restricted` [모듈](module-cpp.md) 특성 없이 IDL 특성을 파일에 지정할 수 있습니다. 컴파일러는 .idl 파일을 생성 하지 않습니다.

- 인 경우 `forced` `restricted` `module` 파일에 IDL 특성이 있는 경우 파일이 특성을 갖도록 요구 하는 후속 특성을 재정의 합니다.

- `push` 현재 **emitidl** 설정을 내부 **emitidl** 스택에 저장 하 고 `pop` **emitidl** 를 내부 **emitidl** 스택의 맨 위에 있는 값으로 설정할 수 있습니다.

`defaultimports=`*부울* \( 필드

- *부울* 인 경우에는 **`true`** 생성 된 .idl 파일로 docobj를 가져옵니다. 또한 소스 코드에 대 한 .h 파일과 이름이 같은 .idl 파일이 `#include` .h 파일과 동일한 디렉터리에 있는 경우 생성 된 .idl 파일에는 해당 .idl 파일에 대 한 import 문이 포함 됩니다.

- *부울* 인 경우에는 **`false`** 생성 된 .idl 파일로 docobj를 가져올 수 없습니다. [가져오기를](import.md)사용 하 여 .idl 파일을 명시적으로 가져와야 합니다.

## <a name="remarks"></a>설명

**Emitidl** c + + 특성을 소스 코드 파일에서 발견 한 후에는 idl 범주 특성이 생성 된 .idl 파일에 배치 됩니다. **Emitidl** 특성이 없으면 소스 코드 파일의 idl 특성이 생성 된 .idl 파일에 출력 됩니다.

소스 코드 파일에 여러 개의 **emitidl** 특성이 있을 수 있습니다. `[emitidl(false)];`이후 파일에이 없으면 `[emitidl(true)];` 생성 된 .idl 파일에 특성이 처리 되지 않습니다.

컴파일러가 새 파일을 발견할 때마다 **emitidl** 은 암시적으로로 설정 됩니다 **`true`** .

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|원하는 위치|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 특성](compiler-attributes.md)<br/>
[독립형 특성](stand-alone-attributes.md)
