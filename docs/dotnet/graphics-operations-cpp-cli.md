---
description: '자세한 정보: 그래픽 작업 (c + +/CLI)'
title: 그래픽 작업(C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- GDI+ [C++]
- .NET Framework [C++], graphics
- images [C++], .NET Framework and
- GDI+ [C++], about graphics operations
- graphics [C++], .NET Framework and
- GDI+ [C++], displaying images
- graphics [C++], displaying images
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
- GDI+ [C++], rotating images
- graphics [C++], rotating images
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: bba27228-b9b3-4c9c-b31c-a04b76702a95
ms.openlocfilehash: 84dbc75aa306219b8733848ece5c594ca40a0489
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223544"
---
# <a name="graphics-operations-ccli"></a>그래픽 작업(C++/CLI)

Windows SDK를 사용 하 여 이미지 조작을 보여 줍니다.

다음 항목에서는 클래스를 사용 하 여 <xref:System.Drawing.Image?displayProperty=fullName> 이미지 조작을 수행 하는 방법을 보여 줍니다.

## <a name="display-images-with-the-net-framework"></a><a name="display"></a> .NET Framework를 사용 하 여 이미지 표시

다음 코드 예제에서는 OnPaint 이벤트 처리기를 수정 하 여 <xref:System.Drawing.Graphics> 기본 폼의 개체에 대 한 포인터를 검색 합니다. <xref:System.Windows.Forms.Form.OnPaint%2A>함수는 Visual Studio 응용 프로그램 마법사를 사용 하 여 만들 가능성이 가장 높은 Windows Forms 응용 프로그램을 위한 것입니다.

이미지는 클래스로 표현 됩니다 <xref:System.Drawing.Image> . 이미지 데이터는 메서드를 사용 하 여 .jpg 파일에서 로드 됩니다. <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> 폼에 이미지를 그리기 전에 이미지 크기를 조정 하 여 이미지를 수용 합니다. 이미지 그리기는 메서드를 사용 하 여 수행 됩니다 <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> .

<xref:System.Drawing.Graphics>및 <xref:System.Drawing.Image> 클래스는 모두 <xref:System.Drawing?displayProperty=fullName> 네임 스페이스에 있습니다.

### <a name="example"></a>예제

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

protected:
virtual Void Form1::OnPaint(PaintEventArgs^ pe) override
{
    Graphics^ g = pe->Graphics;
    Image^ image = Image::FromFile("SampleImage.jpg");
    Form::ClientSize = image->Size;
    g->DrawImage( image, 0, 0, image->Size.Width, image->Size.Height );
}
```

## <a name="draw-shapes-with-the-net-framework"></a><a name="draw"></a> .NET Framework를 사용 하 여 도형 그리기

다음 코드 예제에서는 클래스를 사용 하 여 <xref:System.Drawing.Graphics> 이벤트 처리기를 수정 하 여 <xref:System.Windows.Forms.Form.OnPaint%2A> <xref:System.Drawing.Graphics> 기본 폼의 개체에 대 한 포인터를 검색 합니다. 이 포인터는 폼의 배경색을 설정 하 고 및 메서드를 사용 하 여 선과 호를 그리는 데 사용 <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> 됩니다 <xref:System.Drawing.Graphics.DrawArc%2A> .

### <a name="example"></a>예제

```cpp
#using <system.drawing.dll>
using namespace System;
using namespace System::Drawing;
// ...
protected:
virtual Void Form1::OnPaint(PaintEventArgs^ pe ) override
{
   Graphics^ g = pe->Graphics;
   g->Clear(Color::AntiqueWhite);

   Rectangle rect = Form::ClientRectangle;
   Rectangle smallRect;
   smallRect.X = rect.X + rect.Width / 4;
   smallRect.Y = rect.Y + rect.Height / 4;
   smallRect.Width = rect.Width / 2;
   smallRect.Height = rect.Height / 2;

   Pen^ redPen = gcnew Pen(Color::Red);
   redPen->Width = 4;
   g->DrawLine(redPen, 0, 0, rect.Width, rect.Height);

   Pen^ bluePen = gcnew Pen(Color::Blue);
   bluePen->Width = 10;
   g->DrawArc( bluePen, smallRect, 90, 270 );
}
```

## <a name="rotate-images-with-the-net-framework"></a><a name="rotate"></a> .NET Framework를 사용 하 여 이미지 회전

다음 코드 예제에서는 클래스를 사용 하 여 <xref:System.Drawing.Image?displayProperty=fullName> 디스크에서 이미지를 로드 하 고, 90도 회전 하 고, 새 .jpg 파일로 저장 하는 방법을 보여 줍니다.

### <a name="example"></a>예제

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->RotateFlip( RotateFlipType::Rotate90FlipNone );
   image->Save("SampleImage_rotated.jpg");
   return 0;
}
```

## <a name="convert-image-file-formats-with-the-net-framework"></a><a name="convert"></a> 이미지 파일 형식을 .NET Framework 변환

다음 코드 예제에서는 <xref:System.Drawing.Image?displayProperty=fullName> <xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName> 이미지 파일을 변환 및 저장 하는 데 사용 되는 클래스 및 열거형을 보여 줍니다. 다음 코드는 .jpg 파일에서 이미지를 로드 한 다음 .gif 및 .bmp 파일 형식으로 저장 합니다.

### <a name="example"></a>예제

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;
using namespace System::Drawing::Imaging;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->Save("SampleImage.png", ImageFormat::Png);
   image->Save("SampleImage.bmp", ImageFormat::Bmp);

   return 0;
}
```

## <a name="related-sections"></a>관련 단원

[그래픽 프로그래밍 시작](/dotnet/framework/winforms/advanced/getting-started-with-graphics-programming)

[GDI+ 관리 코드 정보](/dotnet/framework/winforms/advanced/about-gdi-managed-code)

## <a name="see-also"></a>참고 항목

[C + +/CLI를 사용한 .NET 프로그래밍 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

<xref:System.Drawing>
