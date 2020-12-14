---
description: '다음에 대 한 자세한 정보: marshal_as'
title: marshal_as
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshal_as
- msclr.interop.marshal_as
- msclr::interop::marshal_as
helpviewer_keywords:
- marshal_as template [C++]
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
ms.openlocfilehash: 0b0738b8778b287e2e97f074345a10841c70a7b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253626"
---
# <a name="marshal_as"></a>marshal_as

이 메서드는 네이티브 및 관리 되는 환경 간에 데이터를 변환 합니다.

## <a name="syntax"></a>구문

```
To_Type marshal_as<To_Type>(
   From_Type input
);
```

#### <a name="parameters"></a>매개 변수

*input*<br/>
진행 변수로 마샬링할 값 `To_Type` 입니다.

## <a name="return-value"></a>반환 값

변환 된 값인 형식의 변수입니다 `To_Type` `input` .

## <a name="remarks"></a>설명

이 메서드는 네이티브 및 관리 되는 형식 간에 데이터를 변환 하는 간단한 방법입니다. 지원 되는 데이터 형식을 확인 하려면 [c + +의 마샬링 개요](../dotnet/overview-of-marshaling-in-cpp.md)를 참조 하세요. 일부 데이터 변환에는 컨텍스트가 필요 합니다. [Marshal_context 클래스](../dotnet/marshal-context-class.md)를 사용 하 여 이러한 데이터 형식을 변환할 수 있습니다.

지원 되지 않는 데이터 형식 쌍을 마샬링하 려 면 `marshal_as` 는 컴파일 시간에 [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 오류를 생성 합니다. 자세한 내용은이 오류와 함께 제공 된 메시지를 참조 하세요. 더 이상 `C4996` 사용 되지 않는 함수에 대 한 오류를 생성할 수 있습니다. 이에 대 한 한 가지 예는 지원 되지 않는 데이터 형식 쌍을 마샬링하 려 고 합니다.

마샬링 라이브러리는 여러 헤더 파일로 구성 되어 있습니다. 모든 변환에는 하나의 파일만 필요 하지만 다른 변환에 필요한 경우 추가 파일을 포함할 수 있습니다. 파일과 연결 된 변환을 확인 하려면에서 표를 확인 `Marshaling Overview` 합니다. 원하는 변환에 관계 없이 네임 스페이스 요구 사항은 항상 적용 됩니다.

`System::ArgumentNullException(_EXCEPTION_NULLPTR)`입력 매개 변수가 null 인 경우 throw 됩니다.

## <a name="example"></a>예제

이 예제에서는 a를 `const char*` `System::String` 변수 형식으로 마샬링합니다.

```cpp
// marshal_as_test.cpp
// compile with: /clr
#include <stdlib.h>
#include <string.h>
#include <msclr\marshal.h>

using namespace System;
using namespace msclr::interop;

int main() {
   const char* message = "Test String to Marshal";
   String^ result;
   result = marshal_as<String^>( message );
   return 0;
}
```

## <a name="requirements"></a>요구 사항

**헤더 파일:** \<msclr\marshal.h> , \<msclr\marshal_windows.h> , \<msclr\marshal_cppstd.h> 또는 \<msclr\marshal_atl.h>

**네임 스페이스:** msclr:: interop

## <a name="see-also"></a>참고 항목

[C + +의 마샬링 개요](../dotnet/overview-of-marshaling-in-cpp.md)<br/>
[marshal_context 클래스](../dotnet/marshal-context-class.md)
