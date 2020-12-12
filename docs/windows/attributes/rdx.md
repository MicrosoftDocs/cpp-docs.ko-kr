---
description: '자세히 알아보기: rdx'
title: rdx (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: 7d31e33bcc1883bfb787b21ec8f5c1f8bed60208
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329644"
---
# <a name="rdx"></a>rdx

레지스트리 키를 만들거나 기존 레지스트리 키를 수정 합니다.

## <a name="syntax"></a>구문

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>매개 변수

*key*<br/>
만들거나 열 키의 이름입니다.

*valuename*<br/>
필드 설정할 값 필드를 지정 합니다. 이 이름을 가진 값 필드가 키에 아직 없는 경우 추가 됩니다.

*regtype*<br/>
추가 되는 레지스트리 키의 형식입니다. 는 `text` ,, `dword` `binary` 또는 중 하나일 수 `CString` 있습니다.

## <a name="remarks"></a>설명

**Rdx** c + + 특성은 COM 구성 요소에 대 한 기존 레지스트리 키를 만들거나 수정 합니다. 특성은 대상 멤버를 구현 하는 개체에 BEGIN_RDX_MAP 매크로를 추가 합니다. `RegistryDataExchange`BEGIN_RDX_MAP 매크로의 결과로 삽입 된 함수인를 사용 하 여 레지스트리와 데이터 멤버 간에 데이터를 전송할 수 있습니다.

이 특성은 [coclass](coclass.md), [progid](progid.md)또는 [vi_progid](vi-progid.md) 특성 또는 이러한 특성 중 하나를 암시 하는 기타 특성과 함께 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`** 또는 **`struct`** 구성원|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="example"></a>예제

다음 코드는 CMyClass COM 구성 요소를 설명 하는 시스템에 MyValue 라는 레지스트리 키를 추가 합니다.

```cpp
// cpp_attr_ref_rdx.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include "atlbase.h"

[module (name="MyLib")];

class CMyClass {
public:
   CMyClass() {
      strcpy_s(m_sz, "SomeValue");
   }

   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]
   char m_sz[256];
};
```

## <a name="see-also"></a>참고 항목

[COM 특성](com-attributes.md)<br/>
[registration_script](registration-script.md)
