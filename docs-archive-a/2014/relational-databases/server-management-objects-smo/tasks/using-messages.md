---
title: 메시지 사용 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- messages [SMO]
ms.assetid: 4037a866-4826-4c1f-890c-e7e3658adf13
author: stevestein
ms.author: sstein
ms.openlocfilehash: 53b2e0fa4be2dfd53cdd8f4f0cacb7ae0bd79edb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659904"
---
# <a name="using-messages"></a><span data-ttu-id="34484-102">메시지 사용</span><span class="sxs-lookup"><span data-stu-id="34484-102">Using Messages</span></span>
  <span data-ttu-id="34484-103">SMO에서 시스템 메시지는 `Server` 개체에 속하는 <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34484-103">In SMO, system messages are represented by the <xref:Microsoft.SqlServer.Management.Smo.SystemMessageCollection> object that belongs to the `Server` object.</span></span> <span data-ttu-id="34484-104">시스템 메시지는 수정할 수 없으므로 `SystemMessage` 개체 속성은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="34484-104">Because the system messages cannot be modified, `SystemMessage` object properties are read-only.</span></span>  
  
 <span data-ttu-id="34484-105">사용자 정의 메시지는 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection> 개체를 통해 SMO에서 프로그래밍 방식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="34484-105">User-defined messages are represented programmatically in SMO by the <xref:Microsoft.SqlServer.Management.Smo.UserDefinedMessageCollection> object.</span></span> <span data-ttu-id="34484-106">전체 컬렉션을 반복하여 기존 사용자 정의 메시지를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34484-106">Existing user-defined messages can be discovered by iterating through the collection.</span></span> <span data-ttu-id="34484-107">새 사용자 정의 메시지는 새 `UserDefinedMessage` 개체를 인스턴스화하고 적절한 속성을 설정하여 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34484-107">New user-defined messages can be created by instantiating a new `UserDefinedMessage` object and setting the appropriate properties.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="34484-108">예</span><span class="sxs-lookup"><span data-stu-id="34484-108">Examples</span></span>  
 <span data-ttu-id="34484-109">다음 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="34484-109">For the following code examples, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="34484-110">자세한 내용은 visual studio [.net에서 VISUAL BASIC SMO 프로젝트 만들기](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) 및 visual [Studio .Net에서 VISUAL C&#35; smo 프로젝트 만들기](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="34484-110">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="finding-a-particular-system-message-in-visual-basic"></a><span data-ttu-id="34484-111">Visual Basic에서 특정 시스템 메시지 찾기</span><span class="sxs-lookup"><span data-stu-id="34484-111">Finding a Particular System Message in Visual Basic</span></span>  
 <span data-ttu-id="34484-112">코드 예제는 ID 번호로 시스템 메시지를 식별하고 메시지를 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34484-112">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBMessages1](SMO How to#SMO_VBMessages1)]  -->  
  
## <a name="finding-a-particular-system-message-in-visual-c"></a><span data-ttu-id="34484-113">Visual C#에서 특정 시스템 메시지 찾기</span><span class="sxs-lookup"><span data-stu-id="34484-113">Finding a Particular System Message in Visual C#</span></span>  
 <span data-ttu-id="34484-114">코드 예제는 ID 번호로 시스템 메시지를 식별하고 메시지를 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34484-114">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
            //Reference an existing system message using the   
            //ItemByIdAndLanguage method.   
            SystemMessage msg = default(SystemMessage);  
            msg = srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
        }  
```  
  
## <a name="finding-a-particular-system-message-in-powershell"></a><span data-ttu-id="34484-115">PowerShell에서 특정 시스템 메시지 찾기</span><span class="sxs-lookup"><span data-stu-id="34484-115">Finding a Particular System Message in PowerShell</span></span>  
 <span data-ttu-id="34484-116">코드 예제는 ID 번호로 시스템 메시지를 식별하고 메시지를 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34484-116">The code example shows how to identify a system message by ID number and display the message.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Get the message 14126 in US English and display it  
$msg = $srv.SystemMessages.ItemByIdAndLanguage(14126, "us_english")  
$msg.ID.ToString() + " "+ $msg.Text  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-basic"></a><span data-ttu-id="34484-117">Visual Basic에서 새 사용자 정의 메시지 추가</span><span class="sxs-lookup"><span data-stu-id="34484-117">Adding a New User-Defined Message in Visual Basic</span></span>  
 <span data-ttu-id="34484-118">코드 예제는 ID가 5000보다 큰 사용자 정의 메시지를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34484-118">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```vb
Dim mysrv As Server  
mysrv = New Server  
Dim udm As UserDefinedMessage  
udm = New UserDefinedMessage(mysrv, 50003, "us_english", 16, "Test message")  
udm.Create()  
```  
  
## <a name="adding-a-new-user-defined-message-in-visual-c"></a><span data-ttu-id="34484-119">Visual C#에서 새 사용자 정의 메시지 추가</span><span class="sxs-lookup"><span data-stu-id="34484-119">Adding a New User-Defined Message in Visual C#</span></span>  
 <span data-ttu-id="34484-120">코드 예제는 ID가 5000보다 큰 사용자 정의 메시지를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34484-120">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```csharp
{
            Server mysrv = new Server();  
  
            UserDefinedMessage udm = new UserDefinedMessage(mysrv, 50030, "us_english",16, "Test message");  
            udm.Create();  
             UserDefinedMessage  msg = mysrv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
            //Display the message ID and text.   
            Console.WriteLine(msg.ID.ToString() + " " + msg.Text);  
  
        }  
```  
  
## <a name="adding-a-new-user-defined-message-in-powershell"></a><span data-ttu-id="34484-121">PowerShell에서 새 사용자 정의 메시지 추가</span><span class="sxs-lookup"><span data-stu-id="34484-121">Adding a New User-Defined Message in PowerShell</span></span>
 <span data-ttu-id="34484-122">코드 예제는 ID가 5000보다 큰 사용자 정의 메시지를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="34484-122">The code example demonstrates how to create a user-defined message with an ID greater than 50000.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#Create a new message
$udm = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedMessage -ArgumentList `  
$srv, 50030, "us_english", 16, "Test message"  
$udm.Create()  
$msg = $srv.UserDefinedMessages.ItemByIdAndLanguage(50030, "us_english");  
$msg  
```  
