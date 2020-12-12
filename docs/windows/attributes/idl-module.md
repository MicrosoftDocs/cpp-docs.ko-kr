---
description: '다음에 대 한 자세한 정보: idl_module'
title: idl_module (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 01fbb6cb04f31d9df4466e148a89fccb012835e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183141"
---
# <a name="idl_module"></a>idl_module

.Dll 파일의 진입점을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>매개 변수

*name*<br/>
.Idl 파일에 표시 되는 코드 블록의 사용자 정의 이름입니다.

*dllname*<br/>
필드 내보내기가 포함 된 .dll 파일입니다.

*uuid*<br/>
필드 고유 ID입니다.

*helpstring*<br/>
필드 형식 라이브러리를 설명 하는 데 사용 되는 문자열입니다.

*helpstringcontext*<br/>
필드 .Hlp 또는 .chm 파일에 있는 도움말 항목의 ID입니다.

*helpcontext*<br/>
필드 이 형식 라이브러리에 대 한 도움말 ID입니다.

*은선제거*<br/>
필드 라이브러리가 표시 되지 않도록 하는 매개 변수입니다. 자세한 내용은 [hidden](/windows/win32/Midl/hidden) MIDL 특성을 참조하세요.

*액세스가*<br/>
필드 라이브러리의 멤버를 임의로 호출할 수 없습니다. 자세한 내용은 [restricted](/windows/win32/Midl/restricted) MIDL 특성을 참조하세요.

*함수 선언*<br/>
정의 하는 함수입니다.

## <a name="remarks"></a>설명

**Idl_module** c + + 특성을 사용 하면 .dll 파일에서 진입점을 지정 하 여 .dll 파일에서 가져올 수 있습니다.

**Idl_module** 특성은 [module](/windows/win32/Midl/module) MIDL 특성과 비슷한 기능을 포함 합니다.

.Idl 파일의 라이브러리 블록에 DLL 진입점을 추가 하 여 .dll 파일에서 내보낼 수 있는 COM 개체에서 모든 항목을 내보낼 수 있습니다.

는 두 단계로 **idl_module** 를 사용 해야 합니다. 먼저 이름/DLL 쌍을 정의 해야 합니다. 그런 다음 **idl_module** 를 사용 하 여 진입점을 지정 하는 경우 이름 및 추가 특성을 지정 합니다.

## <a name="example"></a>예제

다음 코드에서는 **idl_module** 특성을 사용 하는 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|원하는 위치|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[독립형 특성](stand-alone-attributes.md)<br/>
[엔트리의](entry.md)
