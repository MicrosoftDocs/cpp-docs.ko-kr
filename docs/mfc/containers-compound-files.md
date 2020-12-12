---
description: '자세히 알아보기: 컨테이너: 복합 파일'
title: '컨테이너: 복합 파일'
ms.date: 11/04/2016
helpviewer_keywords:
- compound files [MFC]
- compound documents
- containers [MFC], compound files
- OLE documents [MFC], compound files
- performance [MFC], compound files
- files [MFC], compound
- standardized file structure compound files
- documents [MFC], compound
- documents [MFC], OLE
- OLE containers [MFC], compound files
- access modes for files [MFC]
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
ms.openlocfilehash: d7c7d62569575890afd0f28b803c813a3576f627
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310423"
---
# <a name="containers-compound-files"></a>컨테이너: 복합 파일

이 문서에서는 복합 파일의 구성 요소 및 구현에 대해 설명 하 고 OLE 응용 프로그램에서 복합 파일을 사용 하는 경우의 장점과 단점을 설명 합니다.

복합 파일은 OLE의 필수적인 부분입니다. 데이터 전송 및 OLE 문서 저장소를 용이 하 게 하는 데 사용 됩니다. 복합 파일은 활성 구조적 저장소 모델의 구현입니다. 저장소, 스트림 또는 파일 개체에 대 한 serialization을 지 원하는 일관적인 인터페이스가 있습니다. 복합 파일은 및 클래스에 의해 MFC 라이브러리에서 지원 `COleStreamFile` 됩니다 `COleDocument` .

> [!NOTE]
> 복합 파일을 사용 하는 경우 정보가 OLE 문서 또는 복합 문서에서 제공 되는 것을 의미 하지는 않습니다. 복합 파일은 복합 문서, OLE 문서 및 기타 데이터를 저장 하는 방법 중 하나일 뿐입니다.

## <a name="components-of-a-compound-file"></a><a name="_core_components_of_a_compound_file"></a> 복합 파일의 구성 요소

복합 파일의 OLE 구현은 스트림 개체, 저장소 개체 및 개체의 세 가지 개체 유형을 사용 합니다. `ILockBytes` 이러한 개체는 다음과 같은 방법으로 표준 파일 시스템의 구성 요소와 유사 합니다.

- 파일 같은 스트림 개체는 모든 형식의 데이터를 저장 합니다.

- 디렉터리와 같은 저장소 개체는 다른 저장소 및 스트림 개체를 포함할 수 있습니다.

- `LockBytes` 개체는 저장소 개체와 실제 하드웨어 간의 인터페이스를 나타냅니다. `LockBytes`하드 드라이브나 글로벌 메모리 영역과 같이 개체에 액세스 하는 저장 장치에 실제 바이트를 기록 하는 방법을 결정 합니다. 개체 및 인터페이스에 대 한 자세한 내용은 `LockBytes` `ILockBytes` *OLE 프로그래머 참조* 를 참조 하십시오.

## <a name="advantages-and-disadvantages-of-compound-files"></a><a name="_core_advantages_and_disadvantages_of_compound_files"></a> 복합 파일의 장점 및 단점

복합 파일은 이전 파일 저장소 메서드에서 사용할 수 없는 이점을 제공 합니다. 다음과 같은 변경 내용이 해당됩니다.

- 증분 파일 액세스

- 파일 액세스 모드.

- 파일 구조의 표준화.

응용 프로그램에서 사용 여부를 결정할 때는 복합 파일의 잠재적 단점 (플로피 디스크의 저장소와 관련 된 큰 크기 및 성능 문제)이 고려해 야 합니다.

### <a name="incremental-access-to-files"></a><a name="_core_incremental_access_to_files"></a> 파일에 대 한 증분 액세스

파일에 대 한 증분 액세스는 복합 파일을 사용 하는 경우의 자동 장점입니다. 복합 파일은 파일 내에서 "파일 시스템"으로 볼 수 있으므로 전체 파일을 로드 하지 않고도 스트림이나 저장소와 같은 개별 개체 형식에 액세스할 수 있습니다. 이렇게 하면 응용 프로그램이 사용자가 편집 하기 위해 새 개체에 액세스 하는 데 필요한 시간을 크게 줄일 수 있습니다. 동일한 개념을 기반으로 하는 증분 업데이트는 비슷한 혜택을 제공 합니다. 하나의 개체에 대 한 변경 내용을 저장 하기 위해 전체 파일을 저장 하는 대신 OLE에서 사용자가 편집한 스트림이나 저장소 개체만 저장 합니다.

### <a name="file-access-modes"></a><a name="_core_file_access_modes"></a> 파일 액세스 모드

복합 파일의 개체 변경 내용을 디스크에 커밋하는 경우를 확인할 수 있는 것은 복합 파일을 사용 하는 또 다른 장점입니다. 파일이 액세스 되는 모드 (트랜잭션 또는 직접)는 변경 내용이 커밋되는 시점을 결정 합니다.

- 트랜잭션 모드는 2 단계 커밋 작업을 사용 하 여 복합 파일의 개체를 변경 하 여 사용자가 변경 내용을 저장 하거나 취소 하도록 선택할 때까지 문서의 이전 복사본과 새 복사본을 모두 유지할 수 있습니다.

- 직접 모드는 나중에 실행을 취소 하는 기능 없이 변경 된 문서를 통합 합니다.

액세스 모드에 대 한 자세한 내용은 *OLE 프로그래머 참조* 를 참조 하세요.

### <a name="standardization"></a><a name="_core_standardization"></a> 표준화

복합 파일의 표준화 된 구조를 사용 하면 여러 OLE 응용 프로그램에서 실제로 파일을 만든 응용 프로그램에 대 한 지식 없이 OLE 응용 프로그램에서 만든 복합 파일을 탐색할 수 있습니다.

### <a name="size-and-performance-considerations"></a><a name="_core_size_and_performance_considerations"></a> 크기 및 성능 고려 사항

복합 파일 저장소 구조의 복잡성과 데이터를 증분 방식으로 저장 하는 기능 때문에이 형식을 사용 하는 파일은 비구조적 또는 "플랫 파일" 저장소를 사용 하는 다른 파일 보다 큰 경향이 있습니다. 응용 프로그램에서 자주 파일을 로드 하 고 저장 하는 경우 복합 파일을 사용 하면 파일 크기가 비 복합 파일 보다 훨씬 더 빠르게 증가할 수 있습니다. 복합 파일은 클 수 있기 때문에 플로피 디스크에서 저장 된 파일에 대 한 액세스 시간에도 영향을 줄 수 있으므로 파일에 더 느리게 액세스할 수 있습니다.

성능에 영향을 주는 또 다른 문제는 복합 파일 조각화입니다. 복합 파일의 크기는 파일에서 사용 하는 첫 번째 및 마지막 디스크 섹터의 차이에 따라 결정 됩니다. 조각난 파일은 데이터를 포함 하지 않지만 크기를 계산할 때 계산 되는 사용 가능한 공간의 여러 영역을 포함할 수 있습니다. 복합 파일의 수명 동안 이러한 영역은 저장소 개체의 삽입 또는 삭제에 의해 생성 됩니다.

## <a name="using-compound-files-format-for-your-data"></a><a name="_core_using_compound_files_format_for_your_data"></a> 데이터에 복합 파일 형식 사용

에서 파생 된 문서 클래스를 가진 응용 프로그램을 성공적으로 만들었으면 `COleDocument` 주 문서 생성자가를 호출 하는지 확인 `EnableCompoundFile` 합니다. 응용 프로그램 마법사가 OLE 컨테이너 응용 프로그램을 만드는 경우이 호출이 삽입 됩니다.

*OLE 프로그래머용 참조* 에서 [IStream](/windows/win32/api/objidl/nn-objidl-istream), [IStorage](/windows/win32/api/objidl/nn-objidl-istorage)및 [ILockBytes](/windows/win32/api/objidl/nn-objidl-ilockbytes)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[컨테이너](containers.md)<br/>
[컨테이너: User-Interface 문제](containers-user-interface-issues.md)<br/>
[COleStreamFile 클래스](reference/colestreamfile-class.md)<br/>
[COleDocument 클래스](reference/coledocument-class.md)
