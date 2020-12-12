---
description: '자세한 정보: 방법: 바이트 배열에 대 한 포인터 가져오기'
title: '방법: 바이트 배열에 대한 포인터 가져오기'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, to Byte array
- Byte arrays
ms.assetid: aea18073-3341-47f4-9f0e-04e03327037e
ms.openlocfilehash: d76aa9040be5b908edac3a87ae6f0698f6d6a5dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286386"
---
# <a name="how-to-obtain-a-pointer-to-byte-array"></a>방법: 바이트 배열에 대한 포인터 가져오기

<xref:System.Byte>첫 번째 요소의 주소를 가져와 포인터에 할당 하 여 배열의 배열 블록에 대 한 포인터를 가져올 수 있습니다.

## <a name="example"></a>예제

```cpp
// pointer_to_Byte_array.cpp
// compile with: /clr
using namespace System;
int main() {
   Byte bArr[] = {1, 2, 3};
   Byte* pbArr = &bArr[0];

   array<Byte> ^ bArr2 = gcnew array<Byte>{1,2,3};
   interior_ptr<Byte> pbArr2 = &bArr2[0];
}
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
