---
description: '자세한 정보: STL/CLR 컨테이너 요소에 대 한 요구 사항'
title: STL/CLR 컨테이너 요소에 대한 요구 사항
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
ms.openlocfilehash: 3696d9df40f69b1dd39205a2dc7a3b802e815841
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97305509"
---
# <a name="requirements-for-stlclr-container-elements"></a>STL/CLR 컨테이너 요소에 대한 요구 사항

STL/CLR 컨테이너에 삽입 되는 모든 참조 형식에는 최소한 다음 요소가 있어야 합니다.

- 공용 복사 생성자입니다.

- 공용 할당 연산자입니다.

- Public 소멸자입니다.

또한 [set](../dotnet/set-stl-clr.md) 및 [map](../dotnet/map-stl-clr.md) 과 같은 연관 컨테이너에는 기본적으로 공용 비교 연산자가 정의 되어 있어야 합니다 `operator<` . 컨테이너에 대 한 일부 작업을 수행 하려면 공용 기본 생성자와 공용 동등 연산자를 정의 해야 할 수도 있습니다.

참조 형식, 연관 컨테이너에 삽입할 참조 형식에 대 한 참조 형식 및 핸들에는 정의 된와 같은 비교 연산자가 있어야 합니다 `operator<` . 공용 복사 생성자, public 할당 연산자 및 public 소멸자에 대 한 요구 사항은 값 형식 또는 참조 형식에 대 한 핸들에 대해 존재 하지 않습니다.

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
