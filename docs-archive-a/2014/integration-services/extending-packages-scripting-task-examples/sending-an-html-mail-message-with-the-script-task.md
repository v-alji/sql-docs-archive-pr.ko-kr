---
title: 스크립트 태스크를 사용하여 HTML 메일 메시지 보내기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Send Mail task [Integration Services]
- Script task [Integration Services], examples
- Script task [Integration Services], HTML mail message
ms.assetid: dd2b1eef-b04f-4946-87ab-7bc56bb525ce
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6c1a967b52a84e1ff9c2e54c48e40f4d149b2dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87728500"
---
# <a name="sending-an-html-mail-message-with-the-script-task"></a><span data-ttu-id="526e7-102">스크립트 태스크를 사용하여 HTML 메일 메시지 보내기</span><span class="sxs-lookup"><span data-stu-id="526e7-102">Sending an HTML Mail Message with the Script Task</span></span>
  <span data-ttu-id="526e7-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] SendMail 태스크에서는 일반 텍스트 형식의 메일 메시지만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-103">The [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] SendMail task only supports mail messages in plain text format.</span></span> <span data-ttu-id="526e7-104">그러나 스크립트 태스크와 .NET Framework의 메일 기능을 사용하여 HTML 메일 메시지를 쉽게 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-104">However you can easily send HTML mail messages by using the Script task and the mail capabilities of the .NET Framework.</span></span>

> [!NOTE]
>  <span data-ttu-id="526e7-105">여러 패키지에서 쉽게 다시 사용할 수 있는 태스크를 만들려면 이 스크립트 태스크 예제에 있는 코드를 바탕으로 사용자 지정 태스크를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="526e7-105">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="526e7-106">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="526e7-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>

## <a name="description"></a><span data-ttu-id="526e7-107">Description</span><span class="sxs-lookup"><span data-stu-id="526e7-107">Description</span></span>
 <span data-ttu-id="526e7-108">다음 예에서는 `System.Net.Mail` 네임스페이스를 사용하여 HTML 메일 메시지를 구성하고 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-108">The following example uses the `System.Net.Mail` namespace to configure and send an HTML mail message.</span></span> <span data-ttu-id="526e7-109">스크립트는 패키지 변수에서 전자 메일의 받는 사람, 보내는 사람, 제목 및 본문을 가져오고 이를 사용하여 새 `MailMessag`를 만든 다음 해당 `IsBodyHtml` 속성을 `True`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-109">The script obtains the To, From, Subject, and body of the e-mail from package variables, uses them to create a new `MailMessag`e, and sets its `IsBodyHtml` property to `True`.</span></span> <span data-ttu-id="526e7-110">그런 다음 다른 패키지 변수에서 SMTP 서버 이름을 가져오고 `System.Net.Mail.SmtpClient`의 인스턴스를 초기화한 다음 `Send` 메서드를 호출하여 HTML 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-110">Then it obtains the SMTP server name from another package variable, initializes an instance of `System.Net.Mail.SmtpClient`, and calls its `Send` method to send the HTML message.</span></span> <span data-ttu-id="526e7-111">이 예제에서는 다른 스크립트에서 다시 사용할 수 있도록 메시지 보내기 기능을 서브루틴에 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-111">The sample encapsulates the message sending functionality in a subroutine that could be reused in other scripts.</span></span>

#### <a name="to-configure-this-script-task-example-without-an-smtp-connection-manager"></a><span data-ttu-id="526e7-112">이 스크립트 태스크 예에서 SMTP 연결 관리자를 사용하지 않도록 구성하려면</span><span class="sxs-lookup"><span data-stu-id="526e7-112">To configure this Script Task example without an SMTP Connection Manager</span></span>

1.  <span data-ttu-id="526e7-113">`HtmlEmailTo`, `HtmlEmailFrom` 및 `HtmlEmailSubject`라는 문자열 변수를 만들고 이 변수에 올바른 테스트 메시지에 대한 적절한 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-113">Create string variables named `HtmlEmailTo`, `HtmlEmailFrom`, and `HtmlEmailSubject` and assign appropriate values to them for a valid test message.</span></span>

2.  <span data-ttu-id="526e7-114">`HtmlEmailBody`라는 문자열 변수를 만들고 이 변수에 HTML 태그의 문자열을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-114">Create a string variable named `HtmlEmailBody` and assign a string of HTML markup to it.</span></span> <span data-ttu-id="526e7-115">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-115">For example:</span></span>

    ```
    <html><body><h1>Testing</h1><p>This is a <b>test</b> message.</p></body></html>
    ```

3.  <span data-ttu-id="526e7-116">`HtmlEmailServer`라는 문자열 변수를 만들고 보내는 익명의 보내는 메시지를 허용하는 사용 가능한 SMTP 서버의 이름을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-116">Create a string variable named `HtmlEmailServer` and assign the name of an available SMTP server that accepts anonymous outgoing messages.</span></span>

4.  <span data-ttu-id="526e7-117">이러한 다섯 개의 변수를 모두 새 스크립트 태스크의 **ReadOnlyVariables** 속성에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-117">Assign all five of these variables to the **ReadOnlyVariables** property of a new Script task.</span></span>

5.  <span data-ttu-id="526e7-118">`System.Net` 및 `System.Net.Mail` 네임스페이스를 코드로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-118">Import the `System.Net` and `System.Net.Mail` namespaces into your code.</span></span>

 <span data-ttu-id="526e7-119">이 항목의 예제 코드는 패키지 변수에서 SMTP 서버 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-119">The sample code in this topic obtains the SMTP server name from a package variable.</span></span> <span data-ttu-id="526e7-120">그러나 SMTP 연결 관리자를 사용하여 연결 정보를 캡슐화하고 코드를 통해 연결 관리자에서 서버 이름을 추출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-120">However, you could also take advantage of an SMTP connection manager to encapsulate the connection information, and extract the server name from the connection manager in your code.</span></span> <span data-ttu-id="526e7-121">SMTP 연결 관리자의 <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> 메서드는 문자열을 다음과 같은 형식으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-121">The <xref:Microsoft.SqlServer.Dts.ManagedConnections.SMTPConn.AcquireConnection%2A> method of the SMTP connection manager returns a string in the following format:</span></span>

 `SmtpServer=smtphost;UseWindowsAuthentication=False;EnableSsl=False;`

 <span data-ttu-id="526e7-122">`String.Split` 메서드를 사용하여 이 인수 목록을 각 세미콜론(;) 또는 등호(=) 위치에서 구분하여 개별 문자열의 배열로 만든 다음 해당 배열에서 두 번째 인수(subscript 1)를 서버 이름으로 추출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-122">You can use the `String.Split` method to separate this argument list into an array of individual strings at each semicolon (;) or equal sign (=), and then extract the second argument (subscript 1) from the array as the server name.</span></span>

#### <a name="to-configure-this-script-task-example-with-an-smtp-connection-manager"></a><span data-ttu-id="526e7-123">이 스크립트 태스크 예에서 SMTP 연결 관리자를 사용하도록 구성하려면</span><span class="sxs-lookup"><span data-stu-id="526e7-123">To configure this Script Task example with an SMTP Connection Manager</span></span>

1.  <span data-ttu-id="526e7-124">**ReadOnlyVariables** 목록에서 `HtmlEmailServer` 변수를 제거하여 이전에 구성한 스크립트 태스크를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-124">Modify the Script task configured earlier by removing the `HtmlEmailServer` variable from the list of **ReadOnlyVariables**.</span></span>

2.  <span data-ttu-id="526e7-125">서버 이름을 가져오는 다음 코드 줄을</span><span class="sxs-lookup"><span data-stu-id="526e7-125">Replace the line of code that obtains the server name:</span></span>

    ```
    Dim smtpServer As String = _
      Dts.Variables("HtmlEmailServer").Value.ToString
    ```

     <span data-ttu-id="526e7-126">다음 줄로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="526e7-126">with the following lines:</span></span>

    ```
    Dim smtpConnectionString As String = _
      DirectCast(Dts.Connections("SMTP Connection Manager").AcquireConnection(Dts.Transaction), String)
    Dim smtpServer As String = _
      smtpConnectionString.Split(New Char() {"="c, ";"c})(1)
    ```

## <a name="code"></a><span data-ttu-id="526e7-127">코드</span><span class="sxs-lookup"><span data-stu-id="526e7-127">Code</span></span>

```vb
Public Sub Main()

  Dim htmlMessageTo As String = _
    Dts.Variables("HtmlEmailTo").Value.ToString
  Dim htmlMessageFrom As String = _
    Dts.Variables("HtmlEmailFrom").Value.ToString
  Dim htmlMessageSubject As String = _
    Dts.Variables("HtmlEmailSubject").Value.ToString
  Dim htmlMessageBody As String = _
    Dts.Variables("HtmlEmailBody").Value.ToString
  Dim smtpServer As String = _
    Dts.Variables("HtmlEmailServer").Value.ToString

  SendMailMessage( _
      htmlMessageTo, htmlMessageFrom, _
      htmlMessageSubject, htmlMessageBody, _
      True, smtpServer)

  Dts.TaskResult = ScriptResults.Success

End Sub

Private Sub SendMailMessage( _
    ByVal SendTo As String, ByVal From As String, _
    ByVal Subject As String, ByVal Body As String, _
    ByVal IsBodyHtml As Boolean, ByVal Server As String)

  Dim htmlMessage As MailMessage
  Dim mySmtpClient As SmtpClient

  htmlMessage = New MailMessage( _
    SendTo, From, Subject, Body)
  htmlMessage.IsBodyHtml = IsBodyHtml

  mySmtpClient = New SmtpClient(Server)
  mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials
  mySmtpClient.Send(htmlMessage)

End Sub
```

```csharp
public void Main()
        {

            string htmlMessageTo = Dts.Variables["HtmlEmailTo"].Value.ToString();
            string htmlMessageFrom = Dts.Variables["HtmlEmailFrom"].Value.ToString();
            string htmlMessageSubject = Dts.Variables["HtmlEmailSubject"].Value.ToString();
            string htmlMessageBody = Dts.Variables["HtmlEmailBody"].Value.ToString();
            string smtpServer = Dts.Variables["HtmlEmailServer"].Value.ToString();

            SendMailMessage(htmlMessageTo, htmlMessageFrom, htmlMessageSubject, htmlMessageBody, true, smtpServer);

            Dts.TaskResult = (int)ScriptResults.Success;

        }

        private void SendMailMessage(string SendTo, string From, string Subject, string Body, bool IsBodyHtml, string Server)
        {

            MailMessage htmlMessage;
            SmtpClient mySmtpClient;

            htmlMessage = new MailMessage(SendTo, From, Subject, Body);
            htmlMessage.IsBodyHtml = IsBodyHtml;

            mySmtpClient = new SmtpClient(Server);
            mySmtpClient.Credentials = CredentialCache.DefaultNetworkCredentials;
            mySmtpClient.Send(htmlMessage);

        }
```

<span data-ttu-id="526e7-128">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="526e7-128">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="526e7-129">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="526e7-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="526e7-130">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="526e7-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="526e7-131">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="526e7-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="526e7-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="526e7-132">See Also</span></span>
 [<span data-ttu-id="526e7-133">메일 보내기 태스크</span><span class="sxs-lookup"><span data-stu-id="526e7-133">Send Mail Task</span></span>](../control-flow/send-mail-task.md)


