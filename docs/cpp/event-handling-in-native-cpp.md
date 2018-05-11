---
title: 네이티브 c + +에서 이벤트 처리 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- event handling [C++], Visual C++
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b233c8329119753e5753e19fd641c6bea5d8e42
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="event-handling-in-native-c"></a>네이티브 C++에서 이벤트 처리

네이티브 c + + 이벤트 처리를 설정 하는 이벤트 소스와 이벤트 수신기를 사용 하는 [event_source](../windows/event-source.md) 및 [event_receiver](../windows/event-receiver.md) 특성에 각각 지정 `type` = `native`. 이러한 특성을 사용하면 해당 특성이 적용되는 클래스가 COM 이외의 네이티브 컨텍스트에서 이벤트를 발생시키고 처리할 수 있습니다.

## <a name="declaring-events"></a>이벤트 선언

이벤트 소스 클래스에서 사용 하 여는 [__event](../cpp/event.md) 이벤트로 메서드를 선언 하는 메서드 선언에서 키워드입니다. 메서드를 선언하되 정의하지는 마십시오. 메서드가 이벤트로 만들어질 때 컴파일러가 메서드를 암시적으로 정의하기 때문에 사용자가 메서드를 정의하면 컴파일러 오류가 생성됩니다. 네이티브 이벤트는 매개 변수가 0개 이상인 메서드일 수 있습니다. 반환 형식은 void 또는 모든 정수 계열 형식이 될 수 있습니다.  
  
## <a name="defining-event-handlers"></a>이벤트 처리기 정의

이벤트 수신기 클래스에서는 처리될 이벤트와 일치하는 시그니처(반환 형식, 호출 규칙 및 인수)가 포함된 메서드인 이벤트 처리기를 정의합니다.  
  
## <a name="hooking-event-handlers-to-events"></a>이벤트에 이벤트 처리기 후크  

또한 이벤트 수신기 클래스를 사용 하 여 내장 함수 [__hook](../cpp/hook.md) 이벤트와 이벤트 처리기와 연결할 및 [__unhook](../cpp/unhook.md) 을 이벤트 처리기에서 이벤트를 분리 합니다. 한 이벤트 처리기에 여러 이벤트를 후크하거나 한 이벤트에 여러 이벤트 처리기를 후크할 수 있습니다.  
  
## <a name="firing-events"></a>이벤트 발생  

이벤트를 발생시키려면 이벤트 소스 클래스에서 이벤트로 선언된 메서드를 호출하기만 하면 됩니다. 처리기가 이벤트에 후크된 경우 처리기가 호출됩니다.  
  
### <a name="native-c-event-code"></a>네이티브 C++ 이벤트 코드  

다음 예제에서는 네이티브 C++에서 이벤트를 발생시키는 방법을 보여 줍니다. 예제를 컴파일 및 실행하려면 코드의 주석을 참조하십시오.  
  
## <a name="example"></a>예제  
  
### <a name="code"></a>코드  
  
```cpp  
// evh_native.cpp  
#include <stdio.h>  
  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
  
[event_receiver(native)]  
class CReceiver {  
public:  
   void MyHandler1(int nValue) {  
      printf_s("MyHandler1 was called with value %d.\n", nValue);  
   }  
  
   void MyHandler2(int nValue) {  
      printf_s("MyHandler2 was called with value %d.\n", nValue);  
   }  
  
   void hookEvent(CSource* pSource) {  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
  
   void unhookEvent(CSource* pSource) {  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);  
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);  
   }  
};  
  
int main() {  
   CSource source;  
   CReceiver receiver;  
  
   receiver.hookEvent(&source);  
   __raise source.MyEvent(123);  
   receiver.unhookEvent(&source);  
}  
```  
  
### <a name="output"></a>출력  
  
```Output
MyHandler2 was called with value 123.  
MyHandler1 was called with value 123.  
```  
  
## <a name="see-also"></a>참고 항목

[이벤트 처리](../cpp/event-handling.md)  

