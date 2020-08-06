---
title: SMO 예외 처리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SMO [SQL Server], exceptions
- exceptions [SMO]
- SQL Server Management Objects, exceptions
- inner exceptions [SMO]
ms.assetid: 4c725ff2-6588-44ca-b86a-87979e164153
author: stevestein
ms.author: sstein
ms.openlocfilehash: f4ae9e475a019c9bf874ee3f8365f3f3ac8e19d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660450"
---
# <a name="handling-smo-exceptions"></a><span data-ttu-id="12e44-102">SMO 예외 처리</span><span class="sxs-lookup"><span data-stu-id="12e44-102">Handling SMO Exceptions</span></span>
  <span data-ttu-id="12e44-103">관리 코드에서 오류가 발생하면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-103">In managed code, exceptions are thrown when an error occurs.</span></span> <span data-ttu-id="12e44-104">SMO 메서드와 속성은 반환 값에 성공 또는 실패를 보고하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-104">SMO methods and properties do not report success or failure in the return value.</span></span> <span data-ttu-id="12e44-105">대신 예외 처리기에서 예외를 catch하고 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-105">Instead, exceptions can be caught and handled by an exception handler.</span></span>  
  
 <span data-ttu-id="12e44-106">SMO에는 여러 예외 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-106">Different exception classes exist in the SMO.</span></span> <span data-ttu-id="12e44-107">예외에 대한 텍스트 메시지를 제공하는 `Message` 속성과 같은 예외 속성에서 예외 정보를 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-107">Information about the exception can be extracted from the exception properties such as the `Message` property that gives a text message about the exception.</span></span>  
  
 <span data-ttu-id="12e44-108">예외 처리 문은 프로그래밍 언어와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-108">The exception handling statements are specific to the programming language.</span></span> <span data-ttu-id="12e44-109">예를 들어 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic에서는 `Catch` 문입니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-109">For example, in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic it is the `Catch` statement.</span></span>  
  
## <a name="inner-exceptions"></a><span data-ttu-id="12e44-110">내부 예외</span><span class="sxs-lookup"><span data-stu-id="12e44-110">Inner Exceptions</span></span>  
 <span data-ttu-id="12e44-111">예외는 일반 예외나 특정 예외일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-111">Exceptions can either be general or specific.</span></span> <span data-ttu-id="12e44-112">일반 예외에는 특정 예외 집합이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-112">General exceptions contain a set of specific exceptions.</span></span> <span data-ttu-id="12e44-113">여러 개의 `Catch` 문을 사용하여 예상 오류를 처리하고 나머지 오류가 일반 예외 처리 코드로 이동되게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-113">Several `Catch` statements can be used to handle anticipated errors and let remaining errors fall through to general exception handling code.</span></span> <span data-ttu-id="12e44-114">예외는 연계 시퀀스로 발생하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-114">Exceptions often occur in a cascading sequence.</span></span> <span data-ttu-id="12e44-115">대체로 SQL 예외로 인해 SMO 예외가 발생했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-115">Frequently, an SMO exception might have been caused by an SQL exception.</span></span> <span data-ttu-id="12e44-116">이를 검색하려면 연속해서 `InnerException` 속성을 사용하여 최종 최상위 예외를 발생시킨 원래 예외를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-116">The way to detect this is to use the `InnerException` property successively to determine the original exception that caused the final, top-level exception.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12e44-117">`SQLException`예외는 **system.object** 네임 스페이스에서 선언 됩니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-117">The `SQLException` exception is declared in the **System.Data.SqlClient** namespace.</span></span>  
  
 <span data-ttu-id="12e44-118">![예외 수준을 보여 주는 다이어그램](../../../database-engine/dev-guide/media/exception-flow.gif "예외 수준을 보여 주는 다이어그램")</span><span class="sxs-lookup"><span data-stu-id="12e44-118">![A diagram that shows the levels from which an excp](../../../database-engine/dev-guide/media/exception-flow.gif "A diagram that shows the levels from which an excp")</span></span>  
  
 <span data-ttu-id="12e44-119">다음 다이어그램은 애플리케이션 계층을 통한 예외 흐름을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-119">The diagram shows the flow of exceptions through the layers of the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12e44-120">예제</span><span class="sxs-lookup"><span data-stu-id="12e44-120">Example</span></span>  
 <span data-ttu-id="12e44-121">제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-121">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="12e44-122">자세한 내용은 visual studio [.net에서 Visual C&#35; Smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md) 또는 [visual studio .NET에서 Visual Basic smo 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="12e44-122">For more information, see [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md) or [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="catching-an-exception-in-visual-basic"></a><span data-ttu-id="12e44-123">Visual Basic에서 예외 catch</span><span class="sxs-lookup"><span data-stu-id="12e44-123">Catching an Exception in Visual Basic</span></span>  
 <span data-ttu-id="12e44-124">이 코드 예제에서는 `Try...Catch...Finally`[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 문을 사용하여 SMO 예외를 catch하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-124">This code example shows how to use the `Try...Catch...Finally`[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] statement to catch a SMO exception.</span></span> <span data-ttu-id="12e44-125">모든 SMO 예외는 SmoException 유형이며 SMO 참조에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-125">All SMO exceptions have the type SmoException, and are listed in the SMO reference.</span></span> <span data-ttu-id="12e44-126">내부 예외의 시퀀스가 표시되어 오류의 근원을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-126">The sequence of inner exceptions is displayed to show the root of the error.</span></span> <span data-ttu-id="12e44-127">자세한 내용은 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="12e44-127">For more information, see the [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET documentation.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBExceptions1](SMO How to#SMO_VBExceptions1)]  -->  
  
## <a name="catching-an-exception-in-visual-c"></a><span data-ttu-id="12e44-128">Visual C#에서 예외 catch</span><span class="sxs-lookup"><span data-stu-id="12e44-128">Catching an Exception in Visual C#</span></span>  
 <span data-ttu-id="12e44-129">이 코드 예제에서는 `Try...Catch...Finally` Visual C# 문을 사용하여 SMO 예외를 catch하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-129">This code example shows how to use the `Try...Catch...Finally` Visual C# statement to catch a SMO exception.</span></span> <span data-ttu-id="12e44-130">모든 SMO 예외는 SmoException 유형이며 SMO 참조에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-130">All SMO exceptions have the type SmoException, and are listed in the SMO reference.</span></span> <span data-ttu-id="12e44-131">내부 예외의 시퀀스가 표시되어 오류의 근원을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="12e44-131">The sequence of inner exceptions is displayed to show the root of the error.</span></span> <span data-ttu-id="12e44-132">자세한 내용은 Visual C# 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="12e44-132">For more information, see the Visual C# documentation.</span></span>  
  
```  
{   
//This sample requires the Microsoft.SqlServer.Management.Smo.Agent namespace to be included.   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Define an Operator object variable by supplying the parent SQL Agent and the name arguments in the constructor.   
//Note that the Operator type requires [] parenthesis to differentiate it from a Visual Basic key word.   
op = new Operator(srv.JobServer, "Test_Operator");   
op.Create();   
//Start exception handling.   
try {   
    //Create the operator again to cause an SMO exception.   
    OperatorCategory opx;   
    opx = new OperatorCategory(srv.JobServer, "Test_Operator");   
    opx.Create();   
}   
//Catch the SMO exception   
catch (SmoException smoex) {   
    Console.WriteLine("This is an SMO Exception");   
   //Display the SMO exception message.   
   Console.WriteLine(smoex.Message);   
   //Display the sequence of non-SMO exceptions that caused the SMO exception.   
   Exception ex;   
   ex = smoex.InnerException;   
   while (!object.ReferenceEquals(ex.InnerException, (null))) {   
      Console.WriteLine(ex.InnerException.Message);   
      ex = ex.InnerException;   
    }   
    }   
   //Catch other non-SMO exceptions.   
   catch (Exception ex) {   
      Console.WriteLine("This is not an SMO exception.");   
}   
}  
```  
  
  
