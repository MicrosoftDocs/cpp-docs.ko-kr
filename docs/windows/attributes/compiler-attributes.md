---
title: 컴파일러 특성 (c + + COM) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9f0483676fd0dd60d893f8931511083d369539dd
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791189"
---
# <a name="compiler-attributes"></a>컴파일러 특성

컴파일러 특성 다양 한 기능을 제공합니다.

|특성|설명|
|---------------|-----------------|
|[emitidl](emitidl.md)|모든 후속 IDL 특성 처리 되어 생성된 된.idl 파일에 배치 될 지 여부를 결정 합니다.|
|[event_receiver](event-receiver.md)|이벤트 수신기를 만듭니다.|
|[event_source](event-source.md)|이벤트 소스를 만듭니다.|
|[export](export.md)|.Idl 파일에 배치할 데이터 구조를 하면 됩니다.|
|[구현](implements-cpp.md)|IDL coclass의 구성원으로 강제 적용 되는 디스패치 인터페이스를 지정 합니다.|
|[importidl](importidl.md)|생성된 된.idl 파일에 지정 된.idl 파일을 삽입합니다.|
|[importlib](importlib.md)|다른 형식 라이브러리에 이미 컴파일된 형식을 만들고 있는 형식 라이브러리에서 사용할 수 있도록 합니다.|
|[includelib](includelib-cpp.md)|생성된 된.idl 파일에 포함 될.idl 또는.h 파일을 사용 하면 됩니다.|
|[library_block](library-block.md)|.Idl 파일의 라이브러리 블록 내부 구문을 배치합니다.|
|[no_injected_text](no-injected-text.md)|컴파일러 특성 사용으로 인해 코드를 삽입 하지 못하도록 방지 합니다.|
|[satype](satype.md)|데이터 형식을 지정 합니다 `SAFEARRAY`합니다.|
|[version](version-cpp.md)|인터페이스 또는 클래스의 여러 버전 중에서 특정 버전을 식별합니다.|

## <a name="see-also"></a>참고 항목

[그룹별 특성](attributes-by-group.md)