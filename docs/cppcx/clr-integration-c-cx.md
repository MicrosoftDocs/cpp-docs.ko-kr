---
description: '자세한 정보: CLR 통합 (c + +/CX)'
title: CLR 통합(C++/CX)
ms.date: 01/22/2017
ms.assetid: 76e213cf-2f3d-4181-b35b-9fd25d5b307c
ms.openlocfilehash: ae335168ee456f0461154ab48e9d92325fdc599b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190239"
---
# <a name="clr-integration-ccx"></a>CLR 통합(C++/CX)

일부 Windows 런타임 형식은 c + +/CX에서 특수 처리를 받고 CLR (공용 언어 런타임)을 기반으로 하는 언어를 제공 합니다. 이 문서에서는 한 언어의 여러 형식을 다른 언어에 매핑하는 방법을 설명합니다. 예를 들어 CLR은 Windows.Foundation.IVector를 System.Collections.IList에 매핑하고, Windows.Foundation.IMap를 System.Collections.IDictionary에 매핑합니다. 마찬가지로, c + +/CX는 플랫폼::D 대리자 및 Platform:: String과 같은 형식을 특별히 매핑합니다.

## <a name="mapping-the-windows-runtime-to-ccx"></a>C + +/CX에 Windows 런타임 매핑

C + +/CX가 Windows 메타 데이터 (winmd) 파일을 읽을 때 컴파일러는 일반적인 Windows 런타임 네임 스페이스 및 형식을 c + +/CX 네임 스페이스 및 형식에 자동으로 매핑합니다. 예를 들어 숫자 Windows 런타임 형식은 `UInt32` 자동으로에 매핑됩니다 `default::uint32` .

C + +/CX는 여러 다른 Windows 런타임 형식을 **Platform** 네임 스페이스에 매핑합니다. 예를 들어 읽기 전용 유니코드 텍스트 문자열을 나타내는 **Windows:: Foundation** hstring 핸들은 c + +/cx 클래스에 매핑됩니다 `Platform::String` . Windows 런타임 작업이 오류 HRESULT를 반환 하는 경우 c + +/CX에 매핑됩니다 `Platform::Exception` .

또한 c + +/CX는 Windows 런타임 네임 스페이스의 특정 형식을 매핑하여 형식의 기능을 향상 시킵니다. 이러한 형식의 경우 c + +/CX는 c + +와 관련 된 도우미 생성자 및 메서드를 제공 하며, 형식의 표준 winmd 파일에서 사용할 수 없습니다.

다음 목록에서는 새 생성자 및 도우미 메서드를 지원하는 값 구조체를 보여 줍니다. 구조체 초기화 목록을 사용하는 이전에 작성된 코드가 있으면 새로 추가된 생성자를 사용하도록 이를 변경합니다.

**Windows:: Foundation**

- Point

- Rect

- 크기

**Windows:: UI**

- 색

**Windows:: UI:: Xaml**

- CornerRadius

- 기간

- GridLength

- Thickness

**Windows::UI::Xaml::Interop**

- TypeName

**Windows:: UI:: Xaml:: Media**

- 행렬

**Windows:: UI:: Xaml:: Media:: Animation**

- KeyTime

- RepeatBehavior

**Windows::UI::Xaml::Media::Media3D**

- Matrix3D

## <a name="mapping-the-clr-to-ccx"></a>C + +/CX에 CLR 매핑

Microsoft c + + 또는 c # 컴파일러가 winmd 파일을 읽으면 메타 데이터 파일의 특정 형식을 적절 한 c + +/CX 또는 CLR 형식에 자동으로 매핑합니다. 예를 들어 CLR에서 IVector \<T> 인터페이스는 IList에 매핑됩니다 \<T> . 그러나 c + +/CX에서 IVector \<T> 인터페이스는 다른 형식에 매핑되지 않습니다.

\<T>Windows 런타임의 IReference는 .net에서 Nullable로 매핑됩니다 \<T> .

## <a name="see-also"></a>참고 항목

[다른 언어와의 상호 운용](../cppcx/interoperating-with-other-languages-c-cx.md)
