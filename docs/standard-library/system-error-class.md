---
title: system_error 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- system_error/std::system_error
dev_langs:
- C++
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e81b4a73067d744745621063ed582dfd59e08581
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
---
# <a name="systemerror-class"></a>system_error 클래스

하위 수준 시스템 오류를 보고하기 위해 throw되는 모든 예외에 대한 기본 클래스를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class system_error : public runtime_error {
public:
    explicit system_error(error_code _Errcode,
    const string& _Message = "");

    system_error(error_code _Errcode,
    const char *_Message);

    system_error(error_code::value_type _Errval,
    const error_category& _Errcat,
    const string& _Message);

    system_error(error_code::value_type _Errval,
    const error_category& _Errcat,
    const char *_Message);
const error_code& code() const throw();
const error_code& code() const throw();

};
```

## <a name="remarks"></a>설명

클래스 [exception](../standard-library/exception-class.md)에서 `what`에 의해 반환되는 값은 `_Message` 및 [error_code](../standard-library/error-code-class.md) 형식의 저장된 개체(`code` 또는 `error_code(_Errval, _Errcat)`)에서 생성됩니다.

구성원 함수 `code`는 저장된 [error_code](../standard-library/error-code-class.md) 개체를 반환합니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<system_error>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[<system_error>](../standard-library/system-error.md)<br/>
