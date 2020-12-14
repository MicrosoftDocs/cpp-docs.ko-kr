---
description: '방법: 전역 예외 처리기 정의 및 설치에 대 한 자세한 정보'
title: '방법: 전역 예외 처리기 정의 및 설치'
ms.date: 11/04/2016
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
ms.openlocfilehash: 6747e0bdf95ae4d87ed667576852c282e05a7d6d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258332"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>방법: 전역 예외 처리기 정의 및 설치

다음 코드 예제에서는 처리 되지 않은 예외를 캡처하는 방법을 보여 줍니다. 예제 폼에는 누를 때 null 참조를 수행 하 여 예외가 throw 되는 단추가 포함 되어 있습니다. 이 기능은 일반적인 코드 오류를 나타냅니다. 결과로 생성 되는 예외는 main 함수로 설치 된 응용 프로그램 전체 예외 처리기에 의해 catch 됩니다.

대리자를 이벤트에 바인딩하여이를 수행 <xref:System.Windows.Forms.Application.ThreadException> 합니다. 이 경우 후속 예외가 메서드에 전송 됩니다 `App::OnUnhandled` .

## <a name="example"></a>예제

```cpp
// global_exception_handler.cpp
// compile with: /clr
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Drawing;
using namespace System::Windows::Forms;

ref class MyForm : public Form
{
   Button^ b;
public:
   MyForm( )
   {
      b = gcnew Button( );
      b->Text = "Do Null Access";
      b->Size = Drawing::Size(150, 30);
      b->Click += gcnew EventHandler(this, &MyForm::OnClick);
      Controls->Add(b);
   }
   void OnClick(Object^ sender, EventArgs^ args)
   {
      // do something illegal, like call through a null pointer...
      Object^ o = nullptr;
      o->ToString( );
   }
};

ref class App
{
public:
   static void OnUnhandled(Object^ sender, ThreadExceptionEventArgs^ e)
   {
      MessageBox::Show(e->Exception->Message, "Global Exeception");
      Application::ExitThread( );
   }
};

int main()
{
   Application::ThreadException += gcnew
      ThreadExceptionEventHandler(App::OnUnhandled);

   MyForm^ form = gcnew MyForm( );
   Application::Run(form);
}
```

## <a name="see-also"></a>참고 항목

[예외 처리](../extensions/exception-handling-cpp-component-extensions.md)
