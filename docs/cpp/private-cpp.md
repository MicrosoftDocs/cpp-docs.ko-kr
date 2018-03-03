---
title: private (c + +) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- private_cpp
dev_langs:
- C++
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: baa3a23eacc8428bcbeb6ee5a88a835ff193ee02
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="private-c"></a>private (C++)
## <a name="syntax"></a>구문  
  
```  
private:  
   [member-list]  
private base-class  
```  
  
## <a name="remarks"></a>설명  
 클래스 멤버 목록 앞에 오는 `private` 키워드는 멤버 함수와 클래스의 friend에서만 멤버에 액세스하도록 지정합니다. 이 설정은 다음 액세스 지정자 또는 클래스 끝까지 선언된 모든 멤버에 적용됩니다.  
  
 기본 클래스 이름 앞에 오는 `private` 키워드는 기본 클래스의 공용 및 보호된 멤버가 파생 클래스의 전용 멤버라고 지정합니다.  
  
 클래스에서 멤버의 기본 액세스는 전용입니다. 구조체나 공용 구조체에서 멤버의 기본 액세스는 공용입니다.  
  
 기본 클래스의 기본 액세스는 클래스에 대해 전용이고 구조체에 대해 공용입니다. 공용 구조체에 기본 클래스를 사용할 수 없습니다.  
  
 관련된 정보를 참조 하십시오. [friend](../cpp/friend-cpp.md), [공용](../cpp/public-cpp.md), [보호](../cpp/protected-cpp.md), 멤버 액세스 테이블 및 [클래스멤버에대한액세스제어](member-access-control-cpp.md).  
  
## <a name="clr-specific"></a>/clr 관련  
 CLR 형식에서 c + + 액세스 지정자 키워드 (**공용**, `private`, 및 `protected`) 형식 및 어셈블리와 관련 된 메서드 표시 여부에 영향을 줄 수 있습니다. 자세한 내용은 참조 [멤버 액세스 제어](member-access-control-cpp.md)합니다.  
  
> [!NOTE]
>  으로 컴파일된 파일 [/LN](../build/reference/ln-create-msil-module.md) 이 동작에 의해 영향을 받지 않습니다. 이 경우 관리되는 클래스(공용 또는 전용)가 모두 표시됩니다.  
  
## <a name="end-clr-specific"></a>END /clr 관련  
  
## <a name="example"></a>예  
  
```  
// keyword_private.cpp  
class BaseClass {  
public:  
   // privMem accessible from member function  
   int pubFunc() { return privMem; }  
private:  
   void privMem;  
};  
  
class DerivedClass : public BaseClass {  
public:  
   void usePrivate( int i )  
      { privMem = i; }   // C2248: privMem not accessible  
                         // from derived class  
};  
  
class DerivedClass2 : private BaseClass {  
public:  
   // pubFunc() accessible from derived class  
   int usePublic() { return pubFunc(); }  
};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   DerivedClass2 aDerived2;  
   aBase.privMem = 1;     // C2248: privMem not accessible  
   aDerived.privMem = 1;  // C2248: privMem not accessible  
                          //    in derived class  
   aDerived2.pubFunc();   // C2247: pubFunc() is private in  
                          //    derived class  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [클래스 멤버에 대 한 액세스 제어](member-access-control-cpp.md)   
 [키워드](../cpp/keywords-cpp.md)