---
description: '자세한 정보: 규칙 집합을 사용 하 여 실행할 c + + 규칙 지정'
title: 규칙 집합을 사용하여 실행할 C++ 규칙 지정
ms.date: 07/27/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.native
ms.openlocfilehash: fc1423e92b9dde26b7f6123cae23f1ea4f671fbd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288479"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>규칙 집합을 사용하여 실행할 C++ 규칙 지정

Visual Studio에서 코드 분석과 관련 된 특정 프로젝트 요구 사항을 충족 하도록 사용자 지정 *규칙 집합* 을 만들고 수정할 수 있습니다. 기본 규칙 집합은에 저장 됩니다 *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`* .

**Visual Studio 2017 버전 15.7 이상:** 모든 텍스트 편집기를 사용 하 여 사용자 지정 규칙 집합을 만들고 사용 하는 빌드 시스템에 관계 없이 명령줄 빌드에서 적용할 수 있습니다. 자세한 내용은 [`/analyze:ruleset`](../build/reference/analyze-code-analysis.md)를 참조하세요.

Visual Studio에서 사용자 지정 c + + 규칙 집합을 만들려면 Visual Studio IDE에서 C/c + + 프로젝트를 열어야 합니다. 그런 다음 규칙 집합 편집기에서 표준 규칙 집합을 열고, 특정 규칙을 추가 또는 제거 하 고, 필요에 따라 코드 분석에서 규칙이 위반 된 것으로 확인 될 때 발생 하는 동작을 변경 합니다.

새 사용자 지정 규칙 집합을 만들려면 새 파일 이름을 사용 하 여 저장 합니다. 사용자 지정 규칙 집합이 프로젝트에 자동으로 할당 됩니다.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>기존 규칙 집합 하나에서 사용자 지정 규칙을 만들려면

::: moniker range="<=msvc-150"

1. 솔루션 탐색기에서 프로젝트에 대 한 바로 가기 메뉴를 열고 **속성** 을 선택 합니다.

1. **속성 페이지** 대화 상자에서 **구성 속성** > **코드 분석** > **일반** 속성 페이지를 선택 합니다.

1. **규칙 집합** 드롭다운 목록에서 다음 중 하나를 수행 합니다.

   - 사용자 지정하려는 규칙 집합을 선택합니다.

     \- 또는 -

   - **\<Browse...>** 목록에 없는 기존 규칙 집합을 지정 하려면 선택 합니다.

1. **열기** 를 선택 하 여 규칙 집합 편집기에서 규칙을 표시 합니다.

::: moniker-end
::: moniker range=">=msvc-160"

1. 솔루션 탐색기에서 프로젝트에 대 한 바로 가기 메뉴를 열고 **속성** 을 선택 합니다.

1. **속성 페이지** 대화 상자에서 **구성 속성** > **코드 분석** > **Microsoft** 속성 페이지를 선택 합니다.

1. **활성 규칙** 드롭다운 목록에서 다음 중 하나를 수행 합니다.

   - 사용자 지정하려는 규칙 집합을 선택합니다.

     \- 또는 -

   - **\<Browse...>** 목록에 없는 기존 규칙 집합을 지정 하려면 선택 합니다.

1. **열기** 를 선택 하 여 규칙 집합 편집기에서 규칙을 표시 합니다.

::: moniker-end

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>규칙 집합 편집기에서 규칙 집합을 수정 하려면

- 규칙 집합의 표시 이름을 변경 하려면 **보기** 메뉴에서 **속성 창** 을 선택 합니다. **이름** 상자에 표시 이름을 입력 합니다. 표시 이름은 파일 이름과 다를 수 있습니다.

- 그룹의 모든 규칙을 사용자 지정 규칙 집합에 추가 하려면 그룹의 확인란을 선택 합니다. 그룹의 모든 규칙을 제거 하려면 확인란의 선택을 취소 합니다.

- 사용자 지정 규칙 집합에 특정 규칙을 추가 하려면 규칙의 확인란을 선택 합니다. 규칙 집합에서 규칙을 제거 하려면 확인란의 선택을 취소 합니다.

- 코드 분석에서 규칙을 위반할 때 수행 되는 동작을 변경 하려면 규칙에 대 한 **작업** 필드를 선택 하 고 다음 값 중 하나를 선택 합니다.

     **Warning** -경고를 생성 합니다.

     **오류** -오류를 생성 합니다.

     **정보** -메시지를 생성 합니다.

     **없음** -규칙을 사용 하지 않도록 설정 합니다. 이 동작은 규칙 집합에서 규칙을 제거 하는 것과 같습니다.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>규칙 집합 편집기 도구 모음을 사용 하 여 규칙 집합 편집기에서 필드를 그룹화, 필터링 또는 변경 하려면

- 모든 그룹의 규칙을 확장 하려면 **모두 확장** 을 선택 합니다.

- 모든 그룹의 규칙을 축소 하려면 **모두 축소** 를 선택 합니다.

- 규칙을 그룹화 하는 필드를 변경 하려면 **그룹화** 방법 목록에서 필드를 선택 합니다. 규칙을 그룹화 하지 않고 표시 하려면를 선택 **\<None>** 합니다.

- 규칙 열에서 필드를 추가 하거나 제거 하려면 **열 옵션** 을 선택 합니다.

- 현재 솔루션에 적용 되지 않는 규칙을 숨기려면 **현재 솔루션에 적용 되지 않는 규칙 숨기기** 를 선택 합니다.

- 오류 동작에 할당 된 규칙 표시 및 숨기기를 전환 하려면 **코드 분석 오류를 생성할 수 있는 규칙 표시** 를 선택 합니다.

- 경고 작업에 할당 된 규칙 표시/숨기기를 전환 하려면 **코드 분석 경고를 생성할 수 있는 규칙 표시** 를 선택 합니다.

- **없음** 작업에 할당 된 규칙 표시/숨기기를 전환 하려면 **사용 하도록 설정 되지 않은 규칙 표시** 를 선택 합니다.

- 현재 규칙 집합에 Microsoft 기본 규칙 집합을 추가 하거나 제거 하려면 **자식 규칙 집합 추가 또는 제거** 를 선택 합니다.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>텍스트 편집기에서 규칙 집합을 만들려면

텍스트 편집기에서 사용자 지정 규칙 집합을 만들고, 확장명을 사용 하 여 위치에 저장 하 *`.ruleset`* 고, 컴파일러 옵션을 사용 하 여에 적용할 수 있습니다 [`/analyze:ruleset`](../build/reference/analyze-code-analysis.md) .

다음 예제에서는 시작 지점으로 사용할 수 있는 기본 규칙 집합 파일을 보여 줍니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description="New rules to apply." ToolsVersion="10.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

## <a name="ruleset-schema"></a>규칙 집합 스키마

다음 규칙 집합 스키마는 규칙 집합 파일의 XML 스키마를 설명 합니다. 규칙 집합 스키마는에 저장 됩니다 *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Schemas\RuleSet.xsd`* . 이를 사용 하 여 프로그래밍 방식으로 사용자 지정 규칙 집합을 작성 하거나 사용자 지정 규칙 집합의 형식이 올바른지 여부를 확인할 수 있습니다. 자세한 내용은 [방법: XSD 스키마를 기반으로 XML 문서 만들기](/visualstudio/xml-tools/how-to-create-an-xml-document-based-on-an-xsd-schema)를 참조 하세요.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:annotation>
    <xs:documentation xml:lang="en">
            Visual Studio Code Analysis Rule Set Schema Definition Language.
            Copyright (c) Microsoft Corporation. All rights reserved.
        </xs:documentation>
  </xs:annotation>

  <!-- Every time this file changes, be sure to change the Validate method for the corresponding object in the code -->

  <xs:element name="RuleSet" type="TRuleSet">
  </xs:element>

  <xs:complexType name="TLocalization">
    <xs:all>
      <xs:element name="Name" type="TName" minOccurs="0" maxOccurs="1" />
      <xs:element name="Description" type="TDescription" minOccurs="0" maxOccurs="1" />
    </xs:all>
    <xs:attribute name="ResourceAssembly" type="TNonEmptyString" use="required" />
    <xs:attribute name="ResourceBaseName" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TRuleHintPaths">
    <xs:sequence>
      <xs:element name="Path" type="TNonEmptyString" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="TName">
    <xs:attribute name="Resource" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TDescription">
    <xs:attribute name="Resource" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TInclude">
    <xs:attribute name="Path" type="TNonEmptyString" use="required" />
    <xs:attribute name="Action" type="TIncludeAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TIncludeAll">
    <xs:attribute name="Action" type="TIncludeAllAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TRule">
    <xs:attribute name="Id" type="TNonEmptyString" use="required" />
    <xs:attribute name="Action" type="TRuleAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TRules">
    <xs:sequence>
      <xs:element name="Rule" type="TRule" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="AnalyzerId" type="TNonEmptyString" use="required" />
    <xs:attribute name="RuleNamespace" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TRuleSet">
    <xs:sequence minOccurs="0" maxOccurs="1">
      <xs:element name="Localization" type="TLocalization" minOccurs="0" maxOccurs="1" />
      <xs:element name="RuleHintPaths" type="TRuleHintPaths" minOccurs="0" maxOccurs="1" />
      <xs:element name="IncludeAll" type="TIncludeAll" minOccurs="0" maxOccurs="1" />
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Include" type="TInclude" minOccurs="0" maxOccurs="unbounded" />
        <xs:element name="Rules" type="TRules" minOccurs="0" maxOccurs="unbounded">
          <xs:unique name="UniqueRuleName">
            <xs:selector xpath="Rule" />
            <xs:field xpath="@Id" />
          </xs:unique>
        </xs:element>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="Name" type="TNonEmptyString" use="required" />
    <xs:attribute name="Description" type="xs:string" use="optional" />
    <xs:attribute name="ToolsVersion" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:simpleType name="TRuleAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
      <xs:enumeration value="None"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TIncludeAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
      <xs:enumeration value="None"/>
      <xs:enumeration value="Default"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TIncludeAllAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TNonEmptyString">
    <xs:restriction base="xs:string">
      <xs:minLength value="1" />
    </xs:restriction>
  </xs:simpleType>
  
</xs:schema>

```

스키마 요소 세부 정보:

| Schema 요소 | 설명 |
|--------------------|--------------|
| `TLocalization` | 규칙 집합 파일의 이름, 규칙 집합 파일의 설명, 지역화 된 리소스를 포함 하는 리소스 어셈블리의 이름 및 지역화 된 리소스의 기본 이름을 포함 하는 지역화 정보 |
| `TRuleHintPaths` | 규칙 집합 파일을 검색 하기 위한 힌트로 사용 되는 파일 경로 |
| `TName` | 현재 규칙 집합 파일의 이름입니다. |
| `TDescription` | 현재 규칙 집합 파일의 설명입니다. |
| `TInclude` | 규칙 작업을 포함 하는 포함 된 규칙 집합의 경로 |
| `TIncludeAll` | 모든 규칙에 대 한 규칙 동작 |
| `TRule` | 규칙 동작을 포함 하는 규칙 ID |
| `TRules` | 하나 이상의 규칙 컬렉션 |
| `TRuleSet` | 지역화 정보, 규칙 힌트 경로로 구성 된 규칙 집합 파일 형식으로 모든 정보, 정보 포함, 규칙 정보, 이름, 설명 및 도구 버전 정보를 포함 합니다. |
| `TRuleAction` | 오류, 경고, 정보, 숨김 또는 없음과 같은 규칙 동작을 설명 하는 열거형입니다. |
| `TIncludeAction` | 오류, 경고, 정보, 숨김, 없음 또는 기본값과 같은 규칙 동작을 설명 하는 열거형입니다. |
| `TIncludeAllAction` | 오류, 경고, 정보 또는 숨김과 같은 규칙 동작을 설명 하는 열거형입니다. |

규칙 집합의 예를 보려면 [텍스트 편집기에서 규칙 집합을 만들려면](#to-create-a-rule-set-in-a-text-editor)를 참조 하거나에 저장 된 기본 규칙 집합을 참조 하십시오 `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets` .
