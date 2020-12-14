---
description: '자세한 정보: 스트림 정의'
title: What a Stream Is
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], iostream programming
- data [C++], reading
- streams [C++], in iostream classes
- streams [C++]
ms.assetid: a7e661e9-6cd1-4543-a9a4-c58ee9fd32f3
ms.openlocfilehash: 3786fe05f25949129c1bce63bdbbd73a16209475
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187782"
---
# <a name="what-a-stream-is"></a>What a Stream Is

C++에도 C와 마찬가지로 기본 제공 입력/출력 기능은 없습니다. 하지만, 모든 C++ 컴파일러는 iostream class라고 알려진 체계적이고 객체지향화된 I/O 패키지를 번들로(기본으로) 제공합니다. 스트림은 iostream 클래스의 중요 컨셉입니다. 스트림 객체는 Byte 데이터에 대한 원본과 대상의 역할을 하는 스마트 파일로 간주하면 됩니다. 스크림의 형질(특성)은 클래스 자체와 삽입(Insertion)과 추출(Extraction) 연산자에 의해 커스터마이징됨으로서 결정됩니다.

디스크 운영 시스템은 디바이스 드라이버를 통해, 키보드, 스크린, 프린터 그리고 통신 포트를 마치 확장된 파일인 것 처럼 처리합니다. Iostream 클래스는 이 다수의 확장된 파일과 상호 작용합니다. 내장 클래스들은 Disk I/O와 동일한 Syntax를 이용하여 메모리로부터 읽기와 쓰기를 지원하므로, 스트림 클래스들을 파생하기가 한결 쉬워집니다.

## <a name="in-this-section"></a>섹션 내용

[입력/출력 대체](../standard-library/input-output-alternatives.md)

## <a name="see-also"></a>참고 항목

[iostream 프로그래밍](../standard-library/iostream-programming.md)
