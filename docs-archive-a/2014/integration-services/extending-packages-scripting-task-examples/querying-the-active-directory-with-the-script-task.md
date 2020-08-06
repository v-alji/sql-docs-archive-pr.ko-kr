---
title: 스크립트 태스크를 사용하여 Active Directory 쿼리 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 624aa56289b9cab9174882b586a37e5d0de7ca9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647162"
---
# <a name="querying-the-active-directory-with-the-script-task"></a><span data-ttu-id="2e2d0-102">스크립트 태스크를 사용하여 Active Directory 쿼리</span><span class="sxs-lookup"><span data-stu-id="2e2d0-102">Querying the Active Directory with the Script Task</span></span>
  <span data-ttu-id="2e2d0-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지와 같은 엔터프라이즈 데이터 처리 애플리케이션에서는 Active Directory에 저장된 직원의 직급, 직함 또는 기타 특징에 따라 데이터를 각기 다르게 처리해야 하는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-103">Enterprise data processing applications, such as [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, often need to process data differently based on the rank, job title, or other characteristics of employees stored in Active Directory.</span></span> <span data-ttu-id="2e2d0-104">Active Directory는 사용자에 대한 메타데이터뿐 아니라 컴퓨터 및 프린터와 같은 조직의 기타 자산에 대한 메타데이터도 저장하는 중앙 저장소를 제공하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 디렉터리 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-104">Active Directory is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows directory service that provides a centralized store of metadata, not only about users, but also about other organizational assets such as computers and printers.</span></span> <span data-ttu-id="2e2d0-105">Microsoft .NET Framework의 `System.DirectoryServices` 네임스페이스에서는 Active Directory에 저장된 정보에 따라 데이터 처리 워크플로를 제어할 수 있도록 Active Directory 작업을 위한 클래스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-105">The `System.DirectoryServices` namespace in the Microsoft .NET Framework provides classes for working with Active Directory, to help you direct data processing workflow based on the information that it stores.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e2d0-106">여러 패키지에서 쉽게 다시 사용할 수 있는 태스크를 만들려면 이 스크립트 태스크 예제에 있는 코드를 바탕으로 사용자 지정 태스크를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="2e2d0-107">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="2e2d0-108">Description</span><span class="sxs-lookup"><span data-stu-id="2e2d0-108">Description</span></span>  
 <span data-ttu-id="2e2d0-109">다음 예에서는 직원의 전자 메일 주소가 들어 있는 `email` 변수의 값에 따라 Active Directory에서 직원의 이름, 직함 및 전화 번호를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-109">The following example retrieves an employee's name, title, and phone number from Active Directory based on the value of the `email` variable, which contains the e-mail address of the employee.</span></span> <span data-ttu-id="2e2d0-110">패키지의 선행 제약 조건에서는 검색된 정보를 사용하여 직원의 직함에 따라 낮은 우선 순위의 전자 메일 메시지를 보낼지 높은 우선 순위의 페이지를 보낼지와 같은 사항을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-110">Precedence constraints in the package can use the retrieved information to determine, for example, whether to send a low-priority e-mail message or a high-priority page, based on the job title of the employee.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="2e2d0-111">이 스크립트 태스크 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="2e2d0-111">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="2e2d0-112">`email`, `name` 및 `title`이라는 세 개의 문자열 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-112">Create the three string variables `email`, `name`, and `title`.</span></span> <span data-ttu-id="2e2d0-113">`email` 변수 값으로 올바른 회사 전자 메일 주소를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-113">Enter a valid corporate email address as the value of the `email` variable.</span></span>  
  
2.  <span data-ttu-id="2e2d0-114">**스크립트 태스크 편집기**의 **스크립트** 페이지에서 `email` 속성에 변수를 추가 `ReadOnlyVariables` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-114">On the **Script** page of the **Script Task Editor**, add the `email` variable to the `ReadOnlyVariables` property.</span></span>  
  
3.  <span data-ttu-id="2e2d0-115">`ReadWriteVariables` 속성에 `name` 및 `title` 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-115">Add the `name` and `title` variables to the `ReadWriteVariables` property.</span></span>  
  
4.  <span data-ttu-id="2e2d0-116">스크립트 프로젝트에서 `System.DirectoryServices` 네임스페이스에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-116">In the script project, add a reference to the `System.DirectoryServices` namespace.</span></span>  
  
5.  <span data-ttu-id="2e2d0-117">.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-117">.</span></span> <span data-ttu-id="2e2d0-118">코드에서 `Imports` 문을 사용하여 `DirectoryServices` 네임스페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-118">In your code, use an `Imports` statement to import the `DirectoryServices` namespace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2e2d0-119">이 스크립트를 성공적으로 실행하려면 회사 네트워크에서 Active Directory가 사용되고 있고 이 예에서 사용하는 직원 정보가 회사에 저장되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-119">To run this script successfully, your company must be using Active Directory on its network and storing the employee information that this example uses.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2e2d0-120">코드</span><span class="sxs-lookup"><span data-stu-id="2e2d0-120">Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim directory As DirectoryServices.DirectorySearcher  
    Dim result As DirectoryServices.SearchResult  
    Dim email As String  
  
    email = Dts.Variables("email").Value.ToString  
  
    Try  
        directory = New _  
            DirectoryServices.DirectorySearcher("(mail=" & email & ")")  
        result = directory.FindOne  
        Dts.Variables("name").Value = _  
            result.Properties("displayname").ToString  
        Dts.Variables("title").Value = _  
            result.Properties("title").ToString  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
public void Main()  
{  
    //  
    DirectorySearcher directory;  
    SearchResult result;  
    string email;  
  
    email = (string)Dts.Variables["email"].Value;  
  
    try  
    {  
        directory = new DirectorySearcher("(mail=" + email + ")");  
        result = directory.FindOne();  
        Dts.Variables["name"].Value = result.Properties["displayname"].ToString();  
        Dts.Variables["title"].Value = result.Properties["title"].ToString();  
        Dts.TaskResult = (int)ScriptResults.Success;  
    }  
    catch (Exception ex)  
    {  
        Dts.Events.FireError(0, "Script Task Example", ex.Message + "\n" + ex.StackTrace, String.Empty, 0);  
        Dts.TaskResult = (int)ScriptResults.Failure;  
    }  
  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="2e2d0-121">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="2e2d0-121">External Resources</span></span>  
  
-   <span data-ttu-id="2e2d0-122">social.technet.microsoft.com의 기술 문서 [SSIS에서 Active Directory 정보 처리](https://go.microsoft.com/fwlink/?LinkId=199588)</span><span class="sxs-lookup"><span data-stu-id="2e2d0-122">Technical article, [Processing Active Directory Information in SSIS](https://go.microsoft.com/fwlink/?LinkId=199588), on social.technet.microsoft.com</span></span>  
  
<span data-ttu-id="2e2d0-123">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="2e2d0-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2e2d0-124">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2e2d0-125">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2e2d0-126">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="2e2d0-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
