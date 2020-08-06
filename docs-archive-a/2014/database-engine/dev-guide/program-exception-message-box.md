---
title: 프로그램 예외 메시지 상자 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- exception message box [SQL Server]
- displaying exception message box
ms.assetid: c771985b-149c-459a-b3cb-7b15fde01150
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9d49bdf8c73f86b2c334018d40510b4ae67c85ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741231"
---
# <a name="program-exception-message-box"></a><span data-ttu-id="17d38-102">프로그램 예외 메시지 상자</span><span class="sxs-lookup"><span data-stu-id="17d38-102">Program Exception Message Box</span></span>
  <span data-ttu-id="17d38-103">애플리케이션에서 예외 메시지 상자를 사용하면 <xref:System.Windows.Forms.MessageBox> 클래스에 비해 메시징 환경을 보다 강력하게 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-103">You can use the exception message box in your applications to provide significantly more control over the messaging experience than is provided by the <xref:System.Windows.Forms.MessageBox> class.</span></span> <span data-ttu-id="17d38-104">자세한 내용은 [예외 메시지 상자 프로그래밍](../../../2014/database-engine/dev-guide/exception-message-box-programming.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="17d38-104">For more information, see [Exception Message Box Programming](../../../2014/database-engine/dev-guide/exception-message-box-programming.md).</span></span> <span data-ttu-id="17d38-105">예외 메시지 상자 .dll 가져오기 및 배포에 대한 자세한 내용은 [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="17d38-105">For information about how to obtain and deploy the exception message box .dll, see [Deploying an Exception Message Box Application](../../../2014/database-engine/dev-guide/deploying-an-exception-message-box-application.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="17d38-106">절차</span><span class="sxs-lookup"><span data-stu-id="17d38-106">Procedure</span></span>  
  
#### <a name="to-handle-an-exception-by-using-the-exception-message-box"></a><span data-ttu-id="17d38-107">예외 메시지 상자를 사용하여 예외를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="17d38-107">To handle an exception by using the exception message box</span></span>  
  
1.  <span data-ttu-id="17d38-108">관리 코드 프로젝트의 참조를 Microsoft.ExceptionMessageBox.dll 어셈블리에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-108">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="17d38-109">필드 `using`(C #) 또는 `Imports` ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .net) 지시문을 추가 하 여 <xref:Microsoft.SqlServer.MessageBox> 네임 스페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-109">(Optional) Add a `using` (C#) or `Imports` ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="17d38-110">예상되는 예외를 처리할 try-catch 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-110">Create a try-catch block to handle the anticipated exception.</span></span>  
  
4.  <span data-ttu-id="17d38-111">`catch` 블록 안에 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-111">Within the `catch` block, create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class.</span></span> <span data-ttu-id="17d38-112"><xref:System.Exception>블록에서 처리 하는 개체를 전달 `try` - `catch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-112">Pass the <xref:System.Exception> object handled by the `try`-`catch` block.</span></span>  
  
5.  <span data-ttu-id="17d38-113">(옵션) <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>에 다음 속성 중 하나 이상을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-113">(Optional) Set one or more of the following properties on <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>:</span></span>  
  
    -   <span data-ttu-id="17d38-114"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons>예외 메시지 상자에 표시할 단추를 지정 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-114"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> enumeration that specifies the buttons to display in the exception message box.</span></span>  
  
    -   <span data-ttu-id="17d38-115"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton>예외 메시지 상자의 기본 단추를 지정 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-115"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> enumeration that specifies the default button for the exception message box.</span></span>  
  
    -   <span data-ttu-id="17d38-116"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions>예외 메시지 상자의 다른 동작을 제어 하는 데 사용 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-116"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> enumeration that you use to control other behaviors of the exception message box.</span></span>  
  
    -   <span data-ttu-id="17d38-117"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol>예외 메시지 상자에 표시할 기호를 지정 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-117"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> enumeration that specifies the symbol to display in the exception message box.</span></span>  
  
6.  <span data-ttu-id="17d38-118"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-118">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="17d38-119">예외 메시지 상자가 속해 있는 부모 창을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-119">Pass the parent window to which the exception message box belongs.</span></span>  
  
7.  <span data-ttu-id="17d38-120">(옵션) 사용자가 어느 단추를 클릭했는지 확인하려면 반환된 <xref:System.Windows.Forms.DialogResult> 열거형의 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-120">(Optional) Note the value of returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span>  
  
#### <a name="to-display-the-exception-message-box-without-an-exception"></a><span data-ttu-id="17d38-121">예외 없이 예외 메시지 상자를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="17d38-121">To display the exception message box without an exception</span></span>  
  
1.  <span data-ttu-id="17d38-122">관리 코드 프로젝트의 참조를 Microsoft.ExceptionMessageBox.dll 어셈블리에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-122">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="17d38-123">필드 `using`(C #) 또는 `Imports` (Visual Basic .net) 지시문을 추가 하 여 <xref:Microsoft.SqlServer.MessageBox> 네임 스페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-123">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="17d38-124"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-124">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class.</span></span> <span data-ttu-id="17d38-125">메시지 텍스트를 <xref:System.String> 값으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-125">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="17d38-126">(옵션) <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>에 다음 속성 중 하나 이상을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-126">(Optional) Set one or more of the following properties on <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox>:</span></span>  
  
    -   <span data-ttu-id="17d38-127"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons>예외 메시지 상자에 표시할 단추를 지정 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-127"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons> enumeration that specifies the buttons to display in the exception message box.</span></span>  
  
    -   <span data-ttu-id="17d38-128"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - 예외 메시지 상자의 대화 상자 캡션입니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-128"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Caption%2A> - Dialog box caption of the exception message box.</span></span>  
  
    -   <span data-ttu-id="17d38-129"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton>예외 메시지 상자의 대화 상자에 대 한 기본 단추를 지정 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-129"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.DefaultButton%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDefaultButton> enumeration that specifies the default button for the dialog box of the exception message box.</span></span>  
  
    -   <span data-ttu-id="17d38-130"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions>예외 메시지 상자의 다른 동작을 제어 하는 데 사용 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-130"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Options%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxOptions> enumeration that you use to control other behaviors of the exception message box.</span></span>  
  
    -   <span data-ttu-id="17d38-131"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol>예외 메시지 상자에 표시할 기호를 지정 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-131"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Symbol%2A> - <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxSymbol> enumeration that specifies the symbol to display in the exception message box.</span></span>  
  
5.  <span data-ttu-id="17d38-132"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-132">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="17d38-133">예외 메시지 상자가 속해 있는 부모 창을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-133">Pass the parent window to which the exception message box belongs.</span></span>  
  
6.  <span data-ttu-id="17d38-134">(옵션) 사용자가 어느 단추를 클릭했는지 확인하려면 반환된 <xref:System.Windows.Forms.DialogResult> 열거형의 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-134">(Optional) Note the value of the returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span>  
  
#### <a name="to-display-the-exception-message-box-with-customized-buttons"></a><span data-ttu-id="17d38-135">사용자 지정된 단추와 함께 예외 메시지 상자를 표시하려면</span><span class="sxs-lookup"><span data-stu-id="17d38-135">To display the exception message box with customized buttons</span></span>  
  
1.  <span data-ttu-id="17d38-136">관리 코드 프로젝트의 참조를 Microsoft.ExceptionMessageBox.dll 어셈블리에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-136">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="17d38-137">필드 `using`(C #) 또는 `Imports` (Visual Basic .net) 지시문을 추가 하 여 <xref:Microsoft.SqlServer.MessageBox> 네임 스페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-137">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="17d38-138">다음의 두 가지 방법 중 하나로 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-138">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in one of two ways:</span></span>  
  
    -   <span data-ttu-id="17d38-139"><xref:System.Exception>블록에서 처리 하는 개체를 전달 `try` - `catch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-139">Pass the <xref:System.Exception> object handled by a `try`-`catch` block.</span></span>  
  
    -   <span data-ttu-id="17d38-140">메시지 텍스트를 <xref:System.String> 값으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-140">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="17d38-141"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A>에 다음 값 중 하나를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-141">Set one of the following values for <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Buttons%2A>:</span></span>  
  
    -   <span data-ttu-id="17d38-142"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore>- **중단**, **다시 시도**및 **무시** 단추를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-142"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.AbortRetryIgnore> - displays the **Abort**, **Retry**, and **Ignore** buttons.</span></span>  
  
    -   <span data-ttu-id="17d38-143"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> - 사용자 지정 단추를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-143"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.Custom> - displays custom buttons.</span></span>  
  
    -   <span data-ttu-id="17d38-144"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK>- **확인** 단추를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-144"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OK> - displays the **OK** button.</span></span>  
  
    -   <span data-ttu-id="17d38-145"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel>- **확인** 및 **취소** 단추를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-145"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.OKCancel> - displays the **OK** and **Cancel** buttons.</span></span>  
  
    -   <span data-ttu-id="17d38-146"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel>- **다시 시도** 및 **취소** 단추를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-146"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.RetryCancel> - displays the **Retry** and **Cancel** buttons.</span></span>  
  
    -   <span data-ttu-id="17d38-147"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo>- **예** 및 **아니요** 단추를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-147"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNo> - displays **Yes** and **No** buttons.</span></span>  
  
    -   <span data-ttu-id="17d38-148"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel>- **예**, **아니요**및 **취소** 단추를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-148"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxButtons.YesNoCancel> - displays **Yes**, **No**, and **Cancel** buttons.</span></span>  
  
5.  <span data-ttu-id="17d38-149">(옵션) 사용자 지정 단추를 사용할 경우 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A> 메서드의 오버로드 중 하나를 호출하여 최대 5개의 사용자 지정 단추에 대해 텍스트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-149">(Optional) If you use custom buttons, call one of the overloads of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.SetButtonText%2A> method to specify text for up to five custom buttons.</span></span>  
  
6.  <span data-ttu-id="17d38-150"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-150">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="17d38-151">예외 메시지 상자가 속해 있는 부모 창을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-151">Pass the parent window to which the exception message box belongs.</span></span>  
  
7.  <span data-ttu-id="17d38-152">(옵션) 사용자가 어느 단추를 클릭했는지 확인하려면 반환된 <xref:System.Windows.Forms.DialogResult> 열거형의 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-152">(Optional) Note the value of the returned <xref:System.Windows.Forms.DialogResult> enumeration if you need to determine which button the user clicked.</span></span> <span data-ttu-id="17d38-153">사용자 지정 단추를 사용할 경우 사용자가 어느 사용자 지정 단추를 클릭했는지 확인하려면 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> 속성의 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A> 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-153">If you use custom buttons, note the value of <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBoxDialogResult> for the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CustomDialogResult%2A> property to determine which of the custom buttons the user clicked.</span></span>  
  
#### <a name="to-allow-users-to-decide-whether-to-show-the-exception-message-box"></a><span data-ttu-id="17d38-154">예외 메시지 상자의 표시 여부를 사용자가 결정할 수 있게 하려면</span><span class="sxs-lookup"><span data-stu-id="17d38-154">To allow users to decide whether to show the exception message box</span></span>  
  
1.  <span data-ttu-id="17d38-155">관리 코드 프로젝트의 참조를 Microsoft.ExceptionMessageBox.dll 어셈블리에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-155">Add a reference in your managed code project to the Microsoft.ExceptionMessageBox.dll assembly.</span></span>  
  
2.  <span data-ttu-id="17d38-156">필드 `using`(C #) 또는 `Imports` (Visual Basic .net) 지시문을 추가 하 여 <xref:Microsoft.SqlServer.MessageBox> 네임 스페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-156">(Optional) Add a `using` (C#) or `Imports` (Visual Basic .NET) directive to use the <xref:Microsoft.SqlServer.MessageBox> namespace.</span></span>  
  
3.  <span data-ttu-id="17d38-157">다음의 두 가지 방법 중 하나로 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> 클래스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-157">Create an instance of the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox> class in one of two ways:</span></span>  
  
    -   <span data-ttu-id="17d38-158"><xref:System.Exception>블록에서 처리 하는 개체를 전달 `try` - `catch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-158">Pass the <xref:System.Exception> object handled by a `try`-`catch` block.</span></span>  
  
    -   <span data-ttu-id="17d38-159">메시지 텍스트를 <xref:System.String> 값으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-159">Pass the message text as a <xref:System.String> value.</span></span>  
  
4.  <span data-ttu-id="17d38-160"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> 속성을 `true`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-160">Set the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.ShowCheckbox%2A> property to `true`.</span></span>  
  
5.  <span data-ttu-id="17d38-161">(옵션) 예외 메시지 상자를 다시 표시할지 여부를 사용자에게 묻는 텍스트를 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A>에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-161">(Optional) Specify the text that asks the user to decide whether to show the exception message box again for <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxText%2A>.</span></span> <span data-ttu-id="17d38-162">기본 텍스트는 "이 메시지를 다시 표시 안 함"입니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-162">The default text is "Do not show this message again."</span></span>  
  
6.  <span data-ttu-id="17d38-163">사용자가 선택한 내용을 애플리케이션의 실행 기간 동안에만 유지하려면 <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> 값을 전역 <xref:System.Boolean> 변수로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-163">If you need to keep the user's decision only for the duration of the application's execution, set the value of <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.IsCheckboxChecked%2A> to a global <xref:System.Boolean> variable.</span></span> <span data-ttu-id="17d38-164">예외 메시지 상자의 인스턴스를 만들기 전에 이 값을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="17d38-164">Evaluate this value before creating an instance of the exception message box.</span></span>  
  
7.  <span data-ttu-id="17d38-165">사용자가 선택한 내용을 영구적으로 저장하려면 다음과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-165">If you need to store a user's decision permanently, do the following:</span></span>  
  
    1.  <span data-ttu-id="17d38-166">CreateSubKey 메서드를 호출하여 애플리케이션에서 사용하는 사용자 지정 레지스트리 키를 열고, <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A>를 반환되는 CreateSubKey 개체로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-166">Call the CreateSubKey method to open a custom registry key that your application uses, and set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryKey%2A> to the returned RegistryKey object.</span></span>  
  
    2.  <span data-ttu-id="17d38-167"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A>를 사용되는 레지스트리 값의 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-167">Set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryValue%2A> to the name of the registry value that is used.</span></span>  
  
    3.  <span data-ttu-id="17d38-168"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A>를 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-168">Set <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.CheckboxRegistryMeansDoNotShowDialog%2A> to `true`.</span></span>  
  
    4.  <span data-ttu-id="17d38-169"><xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-169">Call the <xref:Microsoft.SqlServer.MessageBox.ExceptionMessageBox.Show%2A> method.</span></span> <span data-ttu-id="17d38-170">지정된 레지스트리 키가 확인되고, 레지스트리 키에 저장된 데이터가 0인 경우에만 예외 메시지 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-170">The specified registry key is evaluated, and the exception message box is displayed only if the data stored in the registry key is 0.</span></span> <span data-ttu-id="17d38-171">대화 상자가 표시되고 사용자가 단추를 클릭하기 전에 확인란을 선택하면 레지스트리 키의 데이터가 1로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-171">If the dialog box is displayed and the user selects the check box before clicking a button, the data in the registry key is set to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17d38-172">예제</span><span class="sxs-lookup"><span data-stu-id="17d38-172">Example</span></span>  
 <span data-ttu-id="17d38-173">이 예에서는 **확인** 단추만 있는 예외 메시지 상자를 사용하여 처리된 예외 및 추가적인 애플리케이션 관련 정보가 포함된 애플리케이션 예외 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-173">This example uses the exception message box with only the **OK** button to display information from an application exception that includes the handled exception along with additional application-specific information.</span></span>  
  
 [!code-csharp[HowTo#emb_showOKbutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showokbutton)]  
  
 [!code-vb[HowTo#emb_vb_showOKbutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showokbutton)]  
  
## <a name="example"></a><span data-ttu-id="17d38-174">예제</span><span class="sxs-lookup"><span data-stu-id="17d38-174">Example</span></span>  
 <span data-ttu-id="17d38-175">이 예에서는 사용자가 선택할 수 있는 **예** 및 **아니요** 단추가 포함된 예외 메시지 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-175">This example uses the exception message box with **Yes** and **No** buttons from which the user chooses.</span></span>  
  
 [!code-csharp[HowTo#emb_showYesNobutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showyesnobutton)]  
  
 [!code-vb[HowTo#emb_vb_showYesNobutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showyesnobutton)]  
  
## <a name="example"></a><span data-ttu-id="17d38-176">예제</span><span class="sxs-lookup"><span data-stu-id="17d38-176">Example</span></span>  
 <span data-ttu-id="17d38-177">이 예에서는 사용자 지정 단추가 포함된 예외 메시지 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-177">This example uses the exception message box with custom buttons.</span></span>  
  
 [!code-csharp[HowTo#emb_showcustombutton](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_showcustombutton)]  
  
 [!code-vb[HowTo#emb_vb_showcustombutton](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_showcustombutton)]  
  
## <a name="example"></a><span data-ttu-id="17d38-178">예제</span><span class="sxs-lookup"><span data-stu-id="17d38-178">Example</span></span>  
 <span data-ttu-id="17d38-179">이 예에서는 확인란을 사용하여 예외 메시지 상자의 표시 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-179">This example uses the check box to determine whether to show the exception message box.</span></span>  
  
 [!code-csharp[HowTo#emb_usecheckbox](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_usecheckbox)]  
  
 [!code-vb[HowTo#emb_vb_usecheckbox](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_usecheckbox)]  
  
## <a name="example"></a><span data-ttu-id="17d38-180">예제</span><span class="sxs-lookup"><span data-stu-id="17d38-180">Example</span></span>  
 <span data-ttu-id="17d38-181">이 예에서는 확인란과 레지스트리 키를 사용하여 예외 메시지 상자의 표시 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-181">This example uses the check box and a registry key to determine whether to show the exception message box.</span></span>  
  
 [!code-csharp[HowTo#emb_useregkey](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_useregkey)]  
  
 [!code-vb[HowTo#emb_vb_useregkey](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_useregkey)]  
  
## <a name="example"></a><span data-ttu-id="17d38-182">예제</span><span class="sxs-lookup"><span data-stu-id="17d38-182">Example</span></span>  
 <span data-ttu-id="17d38-183">이 예에서는 예외 메시지 상자를 사용하여 문제 해결이나 디버깅에 도움이 되는 추가적인 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17d38-183">This example uses the exception message box to show additional information that is helpful when troubleshooting or debugging.</span></span>  
  
 [!code-csharp[HowTo#emb_moreinfo](../../snippets/csharp/SQL15/replication/howto/cs/embform.cs#emb_moreinfo)]  
  
 [!code-vb[HowTo#emb_vb_moreinfo](../../snippets/visualbasic/SQL15/replication/howto/vb/embform.vb#emb_vb_moreinfo)]  
  
  
