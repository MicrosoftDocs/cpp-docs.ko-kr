---
description: '자세한 정보: Serialization (c + +/CLI)'
title: Serialization(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [C++]
- SerializableAttribute class, managed applications
- NonSerializedAttribute class, managed applications
- managed code [C++], serializing
- .NET Framework [C++], serialization
- serialization [C++], about serialization
ms.assetid: 869010ca-74e1-4989-b409-4643cdb94084
ms.openlocfilehash: 1524ed5d4a000d2006f6f830b1d82119d170c3b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164603"
---
# <a name="serialization-ccli"></a>Serialization(C++/CLI)

관리 되는 클래스 (개별 필드 또는 속성 포함)의 Serialization (개체 또는 멤버의 상태를 영구 미디어에 저장 하는 프로세스)은 및 클래스에서 지원 됩니다 <xref:System.SerializableAttribute> <xref:System.NonSerializedAttribute> .

## <a name="remarks"></a>설명

**SerializableAttribute** 사용자 지정 특성을 관리 되는 클래스에 적용 하 여 전체 클래스를 직렬화 하거나 특정 필드 또는 속성에만 적용 하 여 관리 되는 클래스의 일부를 serialize 합니다. **NonSerializedAttribute** 사용자 지정 특성을 사용 하 여 관리 되는 클래스의 필드 또는 속성을 serialize 하지 않도록 제외 합니다.

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예제에서는 클래스 `MyClass` (및 속성 `m_nCount` )가 serializable로 표시 되어 있습니다. 그러나 속성은 `m_nData` **NonSerialized** 사용자 지정 특성에 의해 표시 된 대로 serialize 되지 않습니다.

### <a name="code"></a>코드

```cpp
// serialization_and_mcpp.cpp
// compile with: /LD /clr
using namespace System;

[ Serializable ]
public ref class MyClass {
public:
   int m_nCount;
private:
   [ NonSerialized ]
   int m_nData;
};
```

### <a name="comments"></a>주석

두 특성 모두 "short name" (**Serializable** 및 **NonSerialized**)을 사용 하 여 참조할 수 있습니다. [특성 적용](/dotnet/standard/attributes/applying-attributes)에서이에 대해 자세히 설명 합니다.

## <a name="see-also"></a>참고 항목

[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
