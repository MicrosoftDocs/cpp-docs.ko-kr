---
description: '자세한 정보: 컴파일러 특성'
title: 컴파일러 특성 (c + + COM)
ms.date: 10/02/2018
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
ms.openlocfilehash: 6d2cbb6bcffb5108ec98fe2786f9fb2216a79b9f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306536"
---
# <a name="compiler-attributes"></a>컴파일러 특성

컴파일러 특성은 다양 한 기능을 제공 합니다.

|특성|설명|
|---------------|-----------------|
|[emitidl](emitidl.md)|모든 후속 IDL 특성을 처리 하 여 생성 된 .idl 파일에 배치할지 여부를 결정 합니다.|
|[event_receiver](event-receiver.md)|이벤트 수신기를 만듭니다.|
|[event_source](event-source.md)|이벤트 소스를 만듭니다.|
|[내보내기가](export.md)|데이터 구조가 .idl 파일에 배치 되도록 합니다.|
|[구현할](implements-cpp.md)|IDL coclass의 멤버가 되도록 강제 적용 되는 디스패치 인터페이스를 지정 합니다.|
|[importidl](importidl.md)|지정 된 .idl 파일을 생성 된 .idl 파일에 삽입 합니다.|
|[importlib](importlib.md)|다른 형식 라이브러리에 이미 컴파일된 형식을 만들고 있는 형식 라이브러리에서 사용할 수 있도록 합니다.|
|[includelib](includelib-cpp.md)|.Idl 또는 .h 파일을 생성 된 .idl 파일에 포함 시킵니다.|
|[library_block](library-block.md)|.Idl 파일의 라이브러리 블록 안에 구문을 배치 합니다.|
|[no_injected_text](no-injected-text.md)|컴파일러가 특성 사용의 결과로 코드를 삽입 하지 않도록 합니다.|
|[satype](satype.md)|의 데이터 형식을 지정 합니다 `SAFEARRAY` .|
|[version](version-cpp.md)|인터페이스 또는 클래스의 여러 버전에서 특정 버전을 식별 합니다.|

## <a name="see-also"></a>참고 항목

[그룹별 특성](attributes-by-group.md)
