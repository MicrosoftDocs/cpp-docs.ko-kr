---
title: collate_byname 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- locale/std::collate_byname
dev_langs:
- C++
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f104736d1c8f9d0ed60f2afd374345ab227300b4
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964914"
---
# <a name="collatebyname-class"></a>collate_byname 클래스

지정된 로캘의 데이터 정렬 패싯으로 사용할 수 있는 개체를 설명하는 파생된 템플릿 클래스입니다. 이 클래스를 사용하여 문자열 정렬 규약과 관련된 문화 영역별 정보를 검색할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>매개 변수

*_Locname* 명명 된 로캘입니다.

*_Refs* 초기 참조 개수입니다.

## <a name="remarks"></a>설명

이 템플릿 클래스는 [collate](../standard-library/collate-class.md#collate)\<CharType> 형식의 [로캘 패싯](../standard-library/locale-class.md#facet_class)으로 사용할 수 있는 개체를 설명합니다. 해당 동작은에 의해 결정 됩니다 합니다 [라는](../standard-library/locale-class.md#name) 로캘 *_Locname*합니다. 각 생성자는 [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`)를 통해 해당 기본 개체를 초기화합니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<locale>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
