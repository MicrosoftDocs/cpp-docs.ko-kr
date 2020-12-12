---
description: '자세한 정보: Override 지정자 (c + +/CLI 및 c + +/CX)'
title: 재정의 지정자(C++/CLI 및 C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- override specifiers, C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
ms.openlocfilehash: ce0b9ad4464eef66bc71826825e8129ef0a24cab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257591"
---
# <a name="override-specifiers--ccli-and-ccx"></a>재정의 지정자(C++/CLI 및 C++/CX)

‘재정의 지정자’는 상속된 형식과 상속된 형식의 멤버가 파생 형식에서 동작하는 방식을 수정합니다.

## <a name="all-runtimes"></a>모든 런타임

### <a name="remarks"></a>설명

재정의 지정자에 대한 자세한 내용은 다음을 참조하십시오.

- [abstract](abstract-cpp-component-extensions.md)

- [new(vtable의 new 슬롯)](new-new-slot-in-vtable-cpp-component-extensions.md)

- [override](override-cpp-component-extensions.md)

- [sealed](sealed-cpp-component-extensions.md)

- [재정의 지정자 및 네이티브 컴파일](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)

**abstract** 및 **sealed** 는 재정의 지정자로 사용되지 않는 형식 선언에서도 유효합니다.

기본 클래스 함수를 명시적으로 재정의하는 방법에 대한 자세한 내용은 [명시적 재정의](explicit-overrides-cpp-component-extensions.md)를 참조하세요.

## <a name="windows-runtime"></a>Windows 런타임

(이 언어 기능에는 Windows 런타임에만 적용되는 설명이 없습니다.)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/ZW`

## <a name="common-language-runtime"></a>공용 언어 런타임

(이 언어 기능에는 공용 언어 런타임에만 적용되는 설명이 없습니다.)

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`

## <a name="see-also"></a>참고 항목

[.NET 및 UWP 용 구성 요소 확장](component-extensions-for-runtime-platforms.md)
