---
description: '자세한 정보: Serialization 메커니즘 무시'
title: Serialization 메커니즘 건너뛰기
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
ms.openlocfilehash: 18d31267ca2dd7760daa839556790af26ff38f6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339776"
---
# <a name="bypassing-the-serialization-mechanism"></a>Serialization 메커니즘 건너뛰기

앞서 살펴본 것 처럼 프레임 워크는 파일에서 데이터를 읽고 쓰는 기본 방법을 제공 합니다. 보관 개체를 통한 직렬화는 뛰어난 많은 응용 프로그램의 요구 사항에 적합 합니다. 이러한 응용 프로그램은 파일을 메모리에 완전히 읽고 사용자가 파일을 업데이트 한 다음 업데이트 된 버전을 디스크에 다시 쓸 수 있도록 합니다.

그러나 일부 응용 프로그램은 데이터에 대해 매우 다르게 작동 하며 이러한 응용 프로그램에 대 한 serialization은 적절 하지 않습니다. 예를 들어 데이터베이스 프로그램, 많은 파일의 일부만 편집 하는 프로그램, 텍스트 전용 파일을 쓰는 프로그램, 데이터 파일을 공유 하는 프로그램 등이 있습니다.

이러한 경우에는 다른 방법으로 [Serialize](reference/cobject-class.md#serialize) 함수를 재정의 하 여 [CArchive](reference/carchive-class.md) 개체가 아닌 [CFile](reference/cfile-class.md) 개체를 통해 파일 작업을 중재 수 있습니다.

`Open`클래스의,,, 및 멤버 함수를 사용 하 여 파일을 열고, 파일 `Read` `Write` `Close` `Seek` `CFile` 포인터 (seek)를 파일의 특정 지점으로 이동 하 고, 해당 지점에서 레코드 (지정 된 바이트 수)를 읽고, 사용자가 레코드를 업데이트 한 다음, 동일한 지점을 다시 검색 하 여 해당 레코드를 파일에 다시 쓸 수 있습니다. 프레임 워크에서는 파일을 열고 `GetFile` 클래스의 멤버 함수를 사용 하 여 개체에 대 한 `CArchive` 포인터를 가져올 수 있습니다 `CFile` . 훨씬 더 정교 하 고 유연한 사용을 위해 클래스의 [Onopendocument](reference/cdocument-class.md#onopendocument) 및 [onsavedocument](reference/cdocument-class.md#onsavedocument) 멤버 함수를 재정의할 수 있습니다 `CWinApp` . 자세한 내용은 *MFC 참조* 의 [CFile](reference/cfile-class.md) 클래스를 참조 하세요.

예를 들어 문서를 `Serialize` 닫을 때 최신 상태로 유지 하기 위해 파일 헤더를 읽고 쓰려는 경우를 제외 하 고 재정의는 아무것도 수행 하지 않습니다.

## <a name="see-also"></a>참고 항목

[문서 사용](using-documents.md)
