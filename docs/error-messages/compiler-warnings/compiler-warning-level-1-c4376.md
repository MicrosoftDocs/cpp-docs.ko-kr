---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4376'
title: 컴파일러 경고(수준 1) C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: 1b91538026ce564e03b2f472f9770d94b4bfc5ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311342"
---
# <a name="compiler-warning-level-1-c4376"></a>컴파일러 경고(수준 1) C4376

액세스 지정자 ' old_specifier: '은 (는) 더 이상 지원 되지 않습니다. 대신 ' new_specifier: '을 사용 하세요.

메타 데이터에서 형식 및 멤버 액세스 가능성을 지정 하는 방법에 대 한 자세한 내용은 [방법: 클래스 및 구조체 정의 및 사용 (c + +/cli)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)의 [형식 표시](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 유형 및 [멤버 표시](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) 유형을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C4376를 생성 합니다.

```cpp
// C4376.cpp
// compile with: /clr /W1 /c
public ref class G {
public public:   // C4376
   void m2();
};

public ref class H {
public:   // OK
   void m2();
};
```
