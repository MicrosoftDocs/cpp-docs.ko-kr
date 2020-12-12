---
description: '자세한 정보: CCustomCommand (CustomRS. H)'
title: CCustomCommand(CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyprovidercommand
- ccustomcommand
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
- CCustomCommand class in CustomRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
ms.openlocfilehash: 35b0e1a1628920a85343a52ce4a003302468884b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170505"
---
# <a name="ccustomcommand-customrsh"></a>CCustomCommand(CustomRS.H)

`CCustomCommand`클래스는 공급자 명령 개체에 대 한 구현입니다. `IAccessor`, 및 인터페이스에 대 한 구현을 제공 합니다 `ICommandText` `ICommandProperties` . `IAccessor`인터페이스는 행 집합의 인터페이스와 동일 합니다. 명령 개체는 접근자를 사용 하 여 매개 변수에 대 한 바인딩을 지정 합니다. 행 집합 개체는이를 사용 하 여 출력 열에 대 한 바인딩을 지정 합니다. `ICommandText`인터페이스는 명령을 텍스트로 지정 하는 유용한 방법입니다. 이 예제에서는 `ICommandText` 나중에 사용자 지정 코드를 추가할 때 인터페이스를 사용 합니다. 또한 메서드를 재정의 합니다 `ICommand::Execute` . `ICommandProperties`인터페이스는 명령 및 행 집합 개체에 대 한 모든 속성을 처리 합니다.

```cpp
// CCustomCommand
class ATL_NO_VTABLE CCustomCommand :
class ATL_NO_VTABLE CCustomCommand :
   public CComObjectRootEx<CComSingleThreadModel>,
   public IAccessorImpl<CCustomCommand>,
   public ICommandTextImpl<CCustomCommand>,
   public ICommandPropertiesImpl<CCustomCommand>,
   public IObjectWithSiteImpl<CCustomCommand>,
   public IConvertTypeImpl<CCustomCommand>,
   public IColumnsInfoImpl<CCustomCommand>
```

`IAccessor`인터페이스는 명령 및 행 집합에 사용 되는 모든 바인딩을 관리 합니다. 소비자는 `IAccessor::CreateAccessor` 구조체의 배열을 사용 하 여를 호출 합니다 `DBBINDING` . 각 `DBBINDING` 구조에는 열 바인딩을 처리 하는 방법에 대 한 정보 (예: 형식 및 길이)가 포함 되어 있습니다. 공급자는 구조를 받은 다음 데이터를 전송 하는 방법과 변환이 필요한 지 여부를 결정 합니다. 인터페이스는 명령 `IAccessor` 개체에서 명령의 매개 변수를 처리 하는 데 사용 됩니다.

Command 개체는 또한의 구현을 제공 `IColumnsInfo` 합니다. OLE DB에 `IColumnsInfo` 인터페이스가 필요 합니다. 인터페이스를 사용 하면 소비자가 명령의 매개 변수에 대 한 정보를 검색할 수 있습니다. 행 집합 개체는 인터페이스를 사용 하 여 `IColumnsInfo` 출력 열에 대 한 정보를 공급자에 게 반환 합니다.

또한 공급자에는 라는 인터페이스가 포함 되어 있습니다 `IObjectWithSite` . `IObjectWithSite`인터페이스는 ATL 2.0에서 구현 되었으며 구현자는 자신에 대 한 정보를 해당 자식에 전달할 수 있도록 합니다. 명령 개체는이 정보를 사용 하 여 `IObjectWithSite` 생성 된 행 집합 개체를 생성 한 사람에 게 알립니다.

## <a name="see-also"></a>참고 항목

[공급자 Wizard-Generated 파일](../../data/oledb/provider-wizard-generated-files.md)
