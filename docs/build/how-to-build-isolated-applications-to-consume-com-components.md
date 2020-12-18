---
description: '자세한 정보: 방법: COM 구성 요소를 사용하는 격리된 애플리케이션 빌드'
title: '방법: COM 구성 요소를 사용하는 격리된 애플리케이션 빌드'
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 31a54683974b8539724ecee24aa45917674a6e82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156387"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>방법: COM 구성 요소를 사용하는 격리된 애플리케이션 빌드

격리된 애플리케이션은 매니페스트가 프로그램에 기본 제공되는 애플리케이션입니다. COM 구성 요소를 사용하는 격리된 애플리케이션을 빌드할 수 있습니다.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>격리된 애플리케이션의 매니페스트에 COM 참조를 추가하려면

1. 격리된 애플리케이션의 프로젝트 속성 페이지를 엽니다.

1. **구성 속성** 노드를 확장한 다음 **매니페스트 도구** 노드를 확장합니다.

1. **격리 COM** 속성 페이지를 선택한 다음 **구성 요소 파일 이름** 속성을 격리된 애플리케이션에서 사용할 COM 구성 요소의 이름으로 설정합니다.

1. **확인** 을 클릭합니다.

### <a name="to-build-manifests-into-isolated-applications"></a>격리된 애플리케이션에 매니페스트를 빌드하려면

1. 격리된 애플리케이션의 프로젝트 속성 페이지를 엽니다.

1. **구성 속성** 노드를 확장한 다음 **매니페스트 도구** 노드를 확장합니다.

1. **입력 및 출력** 속성 페이지를 선택한 후 **매니페스트 포함** 속성을 **예** 로 설정합니다.

1. **확인** 을 클릭합니다.

1. 솔루션을 빌드합니다.

## <a name="see-also"></a>참조

[격리된 애플리케이션](/windows/win32/SbsCs/isolated-applications)<br/>
[Side-by-Side 어셈블리 정보](/windows/win32/SbsCs/about-side-by-side-assemblies-)
