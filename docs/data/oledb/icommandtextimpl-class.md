---
title: ICommandTextImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
ms.openlocfilehash: 7d31933b162a74db31bdd3c65dc68e396a3896c4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501722"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl 클래스

[ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85)) 인터페이스에 대 한 구현을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 된 명령 클래스 `ICommandTextImpl` 입니다.

## <a name="requirements"></a>요구 사항

**헤더:** altdb .h

## <a name="members"></a>멤버

### <a name="interface-methods"></a>인터페이스 메서드

| 속성 | 설명 |
|-|-|
|[GetCommandText](#getcommandtext)|[Setcommandtext](#setcommandtext)에 대 한 마지막 호출로 설정 된 텍스트 명령을 반환 합니다.|
|[SetCommandText](#setcommandtext)|명령 텍스트를 설정 하 여 기존 명령 텍스트를 바꿉니다.|

### <a name="data-members"></a>데이터 멤버

| 속성 | 설명 |
|-|-|
|[m_strCommandText](#strcommandtext)|명령 텍스트를 저장 합니다.|

## <a name="remarks"></a>설명

명령에 대 한 필수 인터페이스입니다.

## <a name="icommandtextimplgetcommandtext"></a><a name="getcommandtext"></a> ICommandTextImpl:: GetCommandText

[Setcommandtext](#setcommandtext)에 대 한 마지막 호출로 설정 된 텍스트 명령을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [ICommandText:: getcommandtext](/previous-versions/windows/desktop/ms709825(v=vs.85)) 를 참조 하세요. *PguidDialect* 매개 변수는 기본적으로 무시 됩니다.

## <a name="icommandtextimplsetcommandtext"></a><a name="setcommandtext"></a> ICommandTextImpl:: SetCommandText

명령 텍스트를 설정 하 여 기존 명령 텍스트를 바꿉니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조*에서 [ICommandText:: setcommandtext](/previous-versions/windows/desktop/ms709757(v=vs.85)) 를 참조 하세요.

## <a name="icommandtextimplm_strcommandtext"></a><a name="strcommandtext"></a> ICommandTextImpl:: m_strCommandText

명령 텍스트 문자열을 저장 합니다.

### <a name="syntax"></a>구문

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
