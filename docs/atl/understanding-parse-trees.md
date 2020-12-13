---
description: '자세한 정보: 구문 분석 트리 이해'
title: ATL 등록자 및 구문 분석 트리
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: cae5256bf932478135db747f80816378e61429a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138244"
---
# <a name="understanding-parse-trees"></a>구문 분석 트리 이해

등록자 스크립트에서 구문 분석 트리를 하나 이상 정의할 수 있습니다. 각 구문 분석 트리는 다음과 같은 형태입니다.

> \<root key>{\<registry expression>}+

여기서

> \<root key> :: = HKEY_CLASSES_ROOT \| HKEY_CURRENT_USER \|\
> &emsp;HKEY_LOCAL_MACHINE \| HKEY_USERS \|\
> &emsp;HKEY_PERFORMANCE_DATA \| HKEY_DYN_DATA \|\
> &emsp;HKEY_CURRENT_CONFIG \| HKCR \| HKCU \|\
> &emsp;HKLM \| HKU \| HKPD \| HKDD \| HKCC

> \<registry expression>::= \<Add Key> \|\<Delete Key>

> \<Add Key>:: = \[ **ForceRemove** \| **NoRemove** \| **val**] \<Key Name> [ \<Key Value> ] [{ \<Add Key> }]

> \<Delete Key> :: = **Delete**\<Key Name>

> \<Key Name> ::= **'**\<AlphaNumeric>+**'**

> \<AlphaNumeric>:: = *NULL이 아닌 모든 문자 (예: ASCII 0* )

> \<Key Value> ::= \<Key Type>\<Key Name>

> \<Key Type> :: = **s** \| **d**

> \<Key Value> ::= **'**\<AlphaNumeric>**'**

> [!NOTE]
> `HKEY_CLASSES_ROOT` 및는 동일 합니다. 및는 `HKCR` `HKEY_CURRENT_USER` `HKCU` 동일 합니다.

구문 분석 트리는 여러 키와 하위 키를에 추가할 수 있습니다 \<root key> . 이렇게 하면 파서가 모든 하위 키의 구문 분석을 완료할 때까지 하위 키의 핸들을 열어 둡니다. 이 방법은 다음 예제에 표시 된 것 처럼 한 번에 단일 키에서 작업 하는 것 보다 효율적입니다.

```rgs
HKEY_CLASSES_ROOT
{
    'MyVeryOwnKey'
    {
        'HasASubKey'
        {
            'PrettyCool'
        }
    }
}
```

여기에서 등록자는 처음에 (만들기)를 엽니다 `HKEY_CLASSES_ROOT\MyVeryOwnKey` . 그런 다음에 하위 키가 있는 것을 볼 수 `MyVeryOwnKey` 있습니다. 등록자는에 대 한 키를 닫지 않고 `MyVeryOwnKey` 핸들을 유지 하 고 `HasASubKey` 이 부모 핸들을 사용 하 여 (만들기)를 엽니다. 부모 핸들이 열려 있지 않으면 시스템 레지스트리 속도가 느려질 수 있습니다. 따라서를 열어서 `HKEY_CLASSES_ROOT\MyVeryOwnKey` `HasASubKey` 부모로 여는 것 `MyVeryOwnKey` 은 열고 `MyVeryOwnKey` 닫는 다음 여는 것 보다 빠릅니다 `MyVeryOwnKey` `MyVeryOwnKey\HasASubKey` .

## <a name="see-also"></a>참고 항목

[등록자 스크립트 만들기](../atl/creating-registrar-scripts.md)
