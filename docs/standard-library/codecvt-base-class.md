---
title: "codecvt_base 클래스 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xlocale/std::codecvt_base
dev_langs:
- C++
helpviewer_keywords:
- codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2b3d1ae1c2bae5c4ce0ab4c7cb6ecadec194f5f9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="codecvtbase-class"></a>codecvt_base 클래스
**result**로 나타내는 열거형을 정의하는 데 사용하는 codecvt 클래스의 기본 클래스입니다. result는 변환 결과를 나타내기 위해 패싯 멤버 함수에 대한 반환 형식으로 사용됩니다.  
  
## <a name="syntax"></a>구문  
  
```
class codecvt_base : public locale::facet {
public:
    enum result {ok, partial, error, noconv};
    codecvt_base( size_t _Refs = 0);
    bool always_noconv() const;
    int max_length() const;
    int encoding() const;
    ~codecvt_base()

protected:
    virtual bool do_always_noconv() const;
    virtual int do_max_length() const;
    virtual int do_encoding() const;
};
```  
  
## <a name="remarks"></a>설명  
 이 클래스는 템플릿 클래스 [codecvt](../standard-library/codecvt-class.md)의 모든 특수화에 공통적인 열거형을 설명합니다. 열거형 결과는 다음과 같이 [do_in](../standard-library/codecvt-class.md#do_in) 또는 [do_out](../standard-library/codecvt-class.md#do_out)의 가능한 반환 값을 설명합니다.  
  
- 내부 문자 인코딩과 외부 문자 인코딩 간 변환에 성공한 경우 **ok**  
  
- 변환이 성공하기에는 대상이 충분히 크지 않은 경우 **partial**  
  
- 소스 시퀀스의 형식이 잘못된 경우 **error**  
  
- 함수가 변환을 수행하지 않은 경우 **noconv**  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<locale>  
  
 **네임스페이스:** std  
  
## <a name="see-also"></a>참고 항목  
 [C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)



