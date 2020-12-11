---
description: '자세한 정보: BNF (Backus-Naur 양식 이해) 구문'
title: ATL 등록자 및 BNF(Backus-Naur 양식) 구문
ms.date: 05/14/2019
helpviewer_keywords:
- BNF notation
- Backus-Naur form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: 7f392d442c4d43865faf9e788f8bf69288673398
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157349"
---
# <a name="understanding-backus-naur-form-bnf-syntax"></a>BNF(Backus-Naur 양식) 구문 이해

ATL 등록자가 사용하는 스크립트는 다음 표에 나와 있는 표기법을 사용하는 BNF 구문을 사용하여 이 항목에 설명되어 있습니다.

|규칙/기호|의미|
|------------------------|-------------|
|::=|해당|
|&#124;|또는|
|X+|하나 이상의 Xs.|
|\[X]|X는 선택 사항입니다. 선택적 구분 기호는 \[]로 표시됩니다.|
|모든 **굵은** 텍스트|문자열 리터럴.|
|모든 *기울임꼴* 텍스트|리터럴 문자열을 생성하는 방법입니다.|

앞의 표에 표시된 것과 같이 등록자 스크립트는 문자열 리터럴을 사용합니다. 이러한 값은 스크립트에 표시되어야 하는 실제 텍스트입니다. 다음 표에서는 ATL 등록자 스크립트에 사용되는 문자열 리터럴을 설명합니다.

|문자열 리터럴|작업|
|--------------------|------------|
|**ForceRemove**|다음 키(있는 경우)를 완전히 제거한 다음, 다시 만듭니다.|
|**NoRemove**|등록 취소 중에는 다음 키를 제거하지 마세요.|
|**짧은**|`<Key Name>`이 실제로 명명된 값임을 지정합니다.|
|**삭제**|등록 중에 다음 키를 삭제합니다.|
|**s**|다음 값이 문자열(REG_SZ)임을 지정합니다.|
|**d**|다음 값이 DWORD(REG_DWORD)임을 지정합니다.|
|**m**|다음 값이 다중 문자열(REG_MULTI_SZ) 임을 지정합니다.|
|**b**|다음 값이 이진값(REG_BINARY)임을 지정합니다.|

## <a name="bnf-syntax-examples"></a>BNF 구문 예제

ATL 등록자 스크립트에서 표기법과 문자열 리터럴이 작동하는 방법을 이해하는 데 도움이 되는 몇 가지 구문 예제가 있습니다.

### <a name="syntax-example-1"></a>구문 예제 1

> \<registry expression> ::= \<Add Key>

`registry expression`이 `Add Key`와 같음을 지정합니다.

### <a name="syntax-example-2"></a>구문 예제 2

> \<registry expression> ::= \<Add Key> | \<Delete Key>

`registry expression`이 `Add Key` 또는 `Delete Key`와 같음을 지정합니다.

### <a name="syntax-example-3"></a>구문 예제 3

> \<Key Name> ::= '\<AlphaNumeric>+'

`Key Name`가 하나 이상의 값과 동일한 지 여부를 지정 합니다 `AlphaNumeric` .

### <a name="syntax-example-4"></a>구문 예제 4

> \<Add Key>:: = [**ForceRemove**  |  **NoRemove**  |  **val**]\<Key Name>

`Add Key`는 `Key Name`과 같고, 문자열 리터럴 `ForceRemove`, `NoRemove` 및 `val`은 선택 사항임을 지정합니다.

### <a name="syntax-example-5"></a>구문 예제 5

> \<AlphaNumeric>:: = *NULL이 아닌 모든 문자 즉, ASCII 0입니다* .

`AlphaNumeric`이 모든 비 NULL 문자와 같음을 나타냅니다.

### <a name="syntax-example-6"></a>구문 예제 6

```rgs
val 'testmulti' = m 'String 1\0String 2\0'
```

키 이름 `testmulti`가 `String 1` 및 `String 2`로 구성된 다중 문자열 값임을 지정합니다.

### <a name="syntax-example-7"></a>구문 예제 7

```rgs
val 'testhex' = d '&H55'
```

키 이름 `testhex`가 16진수 55(10진수 85)로 설정된 DWORD임을 지정합니다. 이 형식은 Visual Basic 사양에 나와 있는 **&H** 표기법을 준수합니다.

## <a name="see-also"></a>참고 항목

[등록자 스크립트 만들기](../atl/creating-registrar-scripts.md)
