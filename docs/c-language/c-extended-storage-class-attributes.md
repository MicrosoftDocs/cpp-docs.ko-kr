---
description: '자세한 정보: C 확장 스토리지 클래스 특성'
title: C 확장 스토리지 클래스 특성
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
ms.openlocfilehash: 9dff43594ef97214609c6ed2195240d0e21648e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168763"
---
# <a name="c-extended-storage-class-attributes"></a>C 확장 스토리지 클래스 특성

**Microsoft 전용**

이 항목의 최신 정보는 [__declspec(C++ 참조)](../cpp/declspec.md)를 참조하세요.

확장된 특성 구문은 Microsoft 전용 C 언어 확장을 단순화 및 표준화합니다. 스토리지 클래스 특성은 thread, naked, dllimport 및 dllexport를 포함하는 확장된 특성 구문을 사용합니다.

스토리지 클래스 정보를 지정하는 확장된 특성 구문은 __declspec 키워드를 사용합니다. 이 키워드는 지정된 형식의 인스턴스가 Microsoft 전용 스토리지 클래스 특성(thread, naked, dllimport 또는 dllexport)과 함께 저장되도록 지정합니다. 다른 스토리지 클래스 한정자의 예로는 static 및 extern 키워드를 들 수 있습니다. 그러나 이러한 키워드는 ANSI C 표준에 속하지 않으므로 확장된 특성 구문에서 다루지 않습니다.

## <a name="syntax"></a>구문

*storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec(** *extended-decl-modifier-seq* **)**  /\* Microsoft 전용 \*/

*extended-decl-modifier-seq*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft 전용\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*extended-decl-modifier*:&nbsp;&nbsp;&nbsp;&nbsp;/\* Microsoft 전용\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`thread`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`naked`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllimport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllexport`**

선언 한정자는 공백으로 구분됩니다. *extended-decl-modifier-seq* 는 비워둘 수 없습니다. 비었을 경우 __declspec는 효과가 없습니다.

thread, naked, dllimport 및 dllexport 스토리지 클래스 특성은 이들이 적용되어 있는 데이터 선언 또는 함수 선언의 속성일 뿐, 함수 자체의 형식 특성을 재정의하지 않습니다. thread 특성은 데이터에만 영향을 줍니다. naked 특성은 함수에만 영향을 줍니다. dllimport 및 dllexport 특성은 함수 및 데이터에 영향을 줍니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[선언 및 형식](../c-language/declarations-and-types.md)
