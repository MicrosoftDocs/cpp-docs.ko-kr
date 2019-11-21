---
title: MFC의 예외 처리
ms.date: 11/19/2019
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: 7d1be30edec598135eed2a74fca87f1e5444f55d
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246726"
---
# <a name="exception-handling-in-mfc"></a>MFC의 예외 처리

This article explains the exception-handling mechanisms available in MFC. Two mechanisms are available:

- C++ exceptions, available in MFC version 3.0 and later

- The MFC exception macros, available in MFC versions 1.0 and later

If you're writing a new application using MFC, you should use the C++ mechanism. You can use the macro-based mechanism if your existing application already uses that mechanism extensively.

You can readily convert existing code to use C++ exceptions instead of the MFC exception macros. Advantages of converting your code and guidelines for doing so are described in the article [Exceptions: Converting from MFC Exception Macros](../mfc/exceptions-converting-from-mfc-exception-macros.md).

If you have already developed an application using the MFC exception macros, you can continue using these macros in your existing code, while using C++ exceptions in your new code. The article [Exceptions: Changes to Exception Macros in Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) gives guidelines for doing so.

> [!NOTE]
>  To enable C++ exception handling in your code, select Enable C++ Exceptions on the Code Generation page in the C/C++ folder of the project's [Property Pages](../build/reference/property-pages-visual-cpp.md) dialog box, or use the [/EHsc](../build/reference/eh-exception-handling-model.md) compiler option.

This article covers the following topics:

- [When to use exceptions](#_core_when_to_use_exceptions)

- [MFC exception support](#_core_mfc_exception_support)

- [Further reading about exceptions](#_core_further_reading_about_exceptions)

##  <a name="_core_when_to_use_exceptions"></a> When to Use Exceptions

Three categories of outcomes can occur when a function is called during program execution: normal execution, erroneous execution, or abnormal execution. Each category is described below.

- Normal execution

   The function may execute normally and return. Some functions return a result code to the caller, which indicates the outcome of the function. The possible result codes are strictly defined for the function and represent the range of possible outcomes of the function. The result code can indicate success or failure or can even indicate a particular type of failure that is within the normal range of expectations. For example, a file-status function can return a code that indicates that the file does not exist. Note that the term "error code" is not used because a result code represents one of many expected outcomes.

- Erroneous execution

   The caller makes some mistake in passing arguments to the function or calls the function in an inappropriate context. This situation causes an error, and it should be detected by an assertion during program development. (For more information on assertions, see [C/C++ Assertions](/visualstudio/debugger/c-cpp-assertions).)

- Abnormal execution

   Abnormal execution includes situations where conditions outside the program's control, such as low memory or I/O errors, are influencing the outcome of the function. Abnormal situations should be handled by catching and throwing exceptions.

Using exceptions is especially appropriate for abnormal execution.

##  <a name="_core_mfc_exception_support"></a> MFC Exception Support

Whether you use the C++ exceptions directly or use the MFC exception macros, you will use [CException Class](../mfc/reference/cexception-class.md) or `CException`-derived objects that may be thrown by the framework or by your application.

The following table shows the predefined exceptions provided by MFC.

|Exception 클래스|의미|
|---------------------|-------------|
|[CMemoryException 클래스](../mfc/reference/cmemoryexception-class.md)|Out-of-memory|
|[CFileException 클래스](../mfc/reference/cfileexception-class.md)|File exception|
|[CArchiveException 클래스](../mfc/reference/carchiveexception-class.md)|Archive/Serialization exception|
|[CNotSupportedException 클래스](../mfc/reference/cnotsupportedexception-class.md)|Response to request for unsupported service|
|[CResourceException 클래스](../mfc/reference/cresourceexception-class.md)|Windows resource allocation exception|
|[CDaoException 클래스](../mfc/reference/cdaoexception-class.md)|Database exceptions (DAO classes)|
|[CDBException 클래스](../mfc/reference/cdbexception-class.md)|Database exceptions (ODBC classes)|
|[COleException 클래스](../mfc/reference/coleexception-class.md)|OLE 예외|
|[COleDispatchException 클래스](../mfc/reference/coledispatchexception-class.md)|Dispatch (automation) exceptions|
|[CUserException 클래스](../mfc/reference/cuserexception-class.md)|Exception that alerts the user with a message box, then throws a generic [CException Class](../mfc/reference/cexception-class.md)|

버전 3.0 이상에서는 MFC가 C++ 예외를 사용했으나 형식에서 C++ 예외와 유사한 이전 예외 처리 매크로를 여전히 지원합니다. 이러한 매크로는 새 프로그래밍에는 권장되지 않지만 여전히 역 호환성에 대해 지원됩니다. 매크로를 이미 사용하는 프로그램에서 자유롭게 C++ 예외를 사용할 수 있습니다. During preprocessing, the macros evaluate to the exception handling keywords defined in the MSVC implementation of the C++ language as of Visual C++ version 2.0. C++ 예외를 사용하는 동안 기존 예외 매크로를 남겨둘 수 있습니다. For information on mixing macros and C++ exception handling and on converting old code to use the new mechanism, see the articles [Exceptions: Using MFC Macros and C++ Exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) and [Exceptions: Converting from MFC Exception Macros](../mfc/exceptions-converting-from-mfc-exception-macros.md). 이전 MFC 예외 매크로를 계속 사용하는 경우 C++ 예외 키워드로 평가합니다. See [Exceptions: Changes to Exception Macros in Version 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md). MFC does not directly support Windows NT structured exception handlers (SEH), as discussed in [Structured Exception Handling](/windows/win32/debug/structured-exception-handling).

##  <a name="_core_further_reading_about_exceptions"></a> Further Reading About Exceptions

The following articles explain using the MFC library for exception handing:

- [예외: 예외 Catch 및 삭제](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [예외: 예외 내용 검사](../mfc/exceptions-examining-exception-contents.md)

- [예외: 예외의 개체 해제](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [예외: 자체 함수에서 예외 Throw](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [예외: 데이터베이스 예외](../mfc/exceptions-database-exceptions.md)

- [예외: OLE 예외](../mfc/exceptions-ole-exceptions.md)

The following articles compare the MFC exception macros with the C++ exception keywords and explain how you can adapt your code:

- [예외: 버전 3.0의 예외 매크로 변경 사항](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [예외: MFC 예외 매크로에서 변환](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [예외: MFC 매크로 및 C++ 예외 사용](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>참조

[Modern C++ best practices for exceptions and error handling](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[How Do I: Create my Own Custom Exception Classes](https://go.microsoft.com/fwlink/p/?linkid=128045)
