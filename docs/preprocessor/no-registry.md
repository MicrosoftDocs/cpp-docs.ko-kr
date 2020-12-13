---
description: '자세한 정보: 특성 가져오기 no_registry'
title: no_registry 가져오기 특성
ms.date: 08/29/2019
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: fa33bf8096a92ec248b0a9d56e39fcc82f433206
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333297"
---
# <a name="no_registry-import-attribute"></a>no_registry 가져오기 특성

**no_registry** 는를 사용 하 여 가져온 형식 라이브러리에 대 한 레지스트리를 검색 하지 않도록 컴파일러에 지시 `#import` 합니다.

## <a name="syntax"></a>Syntax

> **#import** *형식 라이브러리* **no_registry**

### <a name="parameters"></a>매개 변수

*형식 라이브러리*\
형식 라이브러리입니다.

## <a name="remarks"></a>설명

참조 된 형식 라이브러리를 포함 디렉터리에서 찾을 수 없는 경우 형식 라이브러리가 레지스트리에 있는 경우에도 컴파일이 실패 합니다.  **no_registry** 는를 사용 하 여 암시적으로 가져온 다른 형식 라이브러리에 전파 `auto_search` 됩니다.

컴파일러는 파일 이름으로 지정 되 고에 직접 전달 되는 형식 라이브러리에 대해 레지스트리를 검색 하지 않습니다 `#import` .

`auto_search`을 지정 하면 `#import` 초기의 **no_registry** 설정을 사용 하 여 추가 지시문이 생성 됩니다 `#import` . 초기 지시문이 `#import` **no_registry** 되 면 생성 된 `auto_search` `#import` 도 **no_registry** 됩니다.

**no_registry** 는 상호 참조 된 형식 라이브러리를 가져올 때 유용 합니다. 컴파일러가 레지스트리에서 파일의 이전 버전을 찾지 못하도록 합니다. **no_registry** 는 형식 라이브러리가 등록 되어 있지 않은 경우에도 유용 합니다.

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)\
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)
