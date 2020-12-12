---
description: '자세한 정보: Boxing (c + +/CLI)'
title: Boxing(C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: 4914271dc5b1ae0bcee2a82b3cddb4433a2dc84f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282590"
---
# <a name="boxing-ccli"></a>Boxing(C++/CLI)

Boxing은 값 형식을 형식으로 변환 `object` 하거나 값 형식에 의해 구현 되는 임의의 인터페이스 형식으로 변환 하는 프로세스입니다. CLR (공용 언어 런타임)은 값 형식을 boxing 하는 경우의 값을 래핑하고 `System.Object` 관리 되는 힙에 저장 합니다. unboxing하면 개체에서 값 형식이 추출됩니다. Boxing은 암시적이며 unboxing은 명시적입니다.

## <a name="related-articles"></a>관련 문서

|제목|설명|
|-----------|-----------------|
|[방법: 명시적으로 Boxing 요청](../dotnet/how-to-explicitly-request-boxing.md)|변수에 대해 boxing을 명시적으로 요청 하는 방법을 설명 합니다.|
|[방법: gcnew를 사용 하 여 값 형식 만들기 및 암시적 Boxing 사용](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|를 사용 하 여 **`gcnew`** 관리 되는 가비지 수집 힙에 배치할 수 있는 boxed 값 형식을 만드는 방법을 보여 줍니다.|
|[방법: Unbox](../dotnet/how-to-unbox.md)|값을 unbox 하 고 수정 하는 방법을 보여 줍니다.|
|[표준 변환 및 암시적 Boxing](../dotnet/standard-conversions-and-implicit-boxing.md)|Boxing이 필요한 변환에 대해 컴파일러에서 표준 변환을 선택 함을 보여 줍니다.|
|[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Visual C++ 설명서에서 .NET 프로그래밍을 위한 최상위 문서입니다.|
