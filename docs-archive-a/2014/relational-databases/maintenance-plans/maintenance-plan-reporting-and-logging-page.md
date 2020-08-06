---
title: 유지 관리 계획(보고 및 로깅 페이지) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c7a95a7092ce2cdac4aa0540a5cb57d86b48497
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649524"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a><span data-ttu-id="4b568-102">유지 관리 계획(보고 및 로깅 페이지)</span><span class="sxs-lookup"><span data-stu-id="4b568-102">Maintenance Plan (Reporting and Logging Page)</span></span>
  <span data-ttu-id="4b568-103">**보고 및 로깅** 대화 상자를 사용하여 유지 관리 계획이 실행될 때 생성되는 보고서와 로그를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-103">Use the **Reporting and Logging** dialog box to configure the reports and logs that are generated when maintenance plans are executed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4b568-104">옵션</span><span class="sxs-lookup"><span data-stu-id="4b568-104">Options</span></span>  
 <span data-ttu-id="4b568-105">**텍스트 파일 보고서 생성**</span><span class="sxs-lookup"><span data-stu-id="4b568-105">**Generate a text file report**</span></span>  
 <span data-ttu-id="4b568-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 텍스트 파일 보고서를 기록하도록 할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-106">Specify if you want [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to write a text file report.</span></span>  
  
 <span data-ttu-id="4b568-107">**새 파일 만들기**</span><span class="sxs-lookup"><span data-stu-id="4b568-107">**Create a new file**</span></span>  
 <span data-ttu-id="4b568-108">유지 관리 계획이 실행될 때마다 새 보고서 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-108">Create a new report file for each execution of the maintenance plan.</span></span> <span data-ttu-id="4b568-109">기본적으로 보고서 파일은 해당 유지 관리 계획이 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 호스팅하는 컴퓨터의 기본 로그 폴더에 기록됩니다. 기본 로그 폴더는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-109">By default, the report files are written to the computer hosting the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains this maintenance plan, in the folder established as the default log folder during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup.</span></span> <span data-ttu-id="4b568-110">다른 폴더를 지정하려면 **폴더** 입력란에 전체 폴더 경로를 입력하거나 찾아보기 단추( **...** )를 클릭하고 원하는 폴더를 탐색합니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-110">To specify a different folder, enter the full path of the folder in the **Folder** text box, or click the browse button (**...**) and navigate to the desired folder.</span></span>  
  
 <span data-ttu-id="4b568-111">**파일에 추가**</span><span class="sxs-lookup"><span data-stu-id="4b568-111">**Append to file**</span></span>  
 <span data-ttu-id="4b568-112">각각의 계획을 실행하여 생성된 보고서를 **파일 이름** 입력란에 지정된 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-112">Append the report from each plan execution to the file specified in the **File name** text box.</span></span> <span data-ttu-id="4b568-113">찾아보기 단추를 클릭하고 대화 상자에서 파일을 선택하여 파일을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-113">You may also specify a file by clicking the browse button and selecting a file from the dialog box.</span></span>  
  
 <span data-ttu-id="4b568-114">**전자 메일 받는 사람에게 보고서 보내기**</span><span class="sxs-lookup"><span data-stu-id="4b568-114">**Send report to an e-mail recipient**</span></span>  
 <span data-ttu-id="4b568-115">유지 관리 계획의 실행 결과를 전자 메일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-115">Transmit the outcome of a maintenance plan execution via e-mail.</span></span> <span data-ttu-id="4b568-116">이 옵션은 데이터베이스 메일을 활성화하고 적절히 구성한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-116">This option is only available if Database Mail is enabled and properly configured.</span></span>  
  
 <span data-ttu-id="4b568-117">**에이전트 운영자**</span><span class="sxs-lookup"><span data-stu-id="4b568-117">**Agent operator**</span></span>  
 <span data-ttu-id="4b568-118">전자 메일을 받는 에이전트 운영자를 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-118">Select an agent operator from the list who will be the recipient of the e-mail.</span></span> <span data-ttu-id="4b568-119">이 옵션은 메일을 활성화하고 적절히 구성한 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-119">This option is only available if mail is enabled and properly</span></span>  
  
 <span data-ttu-id="4b568-120">**확장 정보 기록**</span><span class="sxs-lookup"><span data-stu-id="4b568-120">**Log extended information**</span></span>  
 <span data-ttu-id="4b568-121">로그에 추가 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-121">Include more information in the log.</span></span> <span data-ttu-id="4b568-122">이 옵션을 선택하면 저장되는 유지 관리 계획 기록의 크기가 커집니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-122">Including this option will increase the size of the stored maintenance plan history.</span></span>  
  
 <span data-ttu-id="4b568-123">**원격 서버에 기록**</span><span class="sxs-lookup"><span data-stu-id="4b568-123">**Log to remote server**</span></span>  
 <span data-ttu-id="4b568-124">원격 서버에 유지 관리 계획 기록을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-124">Logs maintenance plan history to a remote server.</span></span>  
  
 <span data-ttu-id="4b568-125">**연결**</span><span class="sxs-lookup"><span data-stu-id="4b568-125">**Connection**</span></span>  
 <span data-ttu-id="4b568-126">원격 서버에 기록할 때 사용할 연결 정보를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-126">Specifies the connection information to use when logging to a remote server.</span></span>  
  
 <span data-ttu-id="4b568-127">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="4b568-127">**New**</span></span>  
 <span data-ttu-id="4b568-128">**연결 속성** 대화 상자를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-128">Displays the **Connection Properties** dialog box.</span></span> <span data-ttu-id="4b568-129">원격 서버에 기록할 때 사용할 새 연결 정보를 구성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b568-129">Used to configure new connection information for logging to a remote server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b568-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4b568-130">See Also</span></span>  
 <span data-ttu-id="4b568-131">[유지 관리 계획](maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="4b568-131">[Maintenance Plans](maintenance-plans.md) </span></span>  
 [<span data-ttu-id="4b568-132">데이터베이스 메일</span><span class="sxs-lookup"><span data-stu-id="4b568-132">Database Mail</span></span>](../database-mail/database-mail.md)  
  
  
