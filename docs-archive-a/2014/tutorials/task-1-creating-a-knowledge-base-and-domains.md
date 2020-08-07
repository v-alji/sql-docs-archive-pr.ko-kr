---
title: '작업 1: 기술 자료 및 도메인 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 7d74a60b-8933-4038-bcbb-4e9dcc4f70e9
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ce1b22e3d677e831a1d518dacc1267ad0e6be236
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731247"
---
# <a name="task-1-creating-a-knowledge-base-and-domains"></a><span data-ttu-id="2206a-102">태스크 1: 기술 자료 및 도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="2206a-102">Task 1: Creating a Knowledge Base and Domains</span></span>
  <span data-ttu-id="2206a-103">이 태스크에서는 **Suppliers** 기술 자료를 만들고 데이터를 정리 하 고 데이터를 일치 시켜 중복 항목을 제거 하는 데 사용 되는 도메인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-103">In this task, you create the **Suppliers** knowledge base and create domains that is used for cleansing data and matching data to remove duplicates.</span></span>  
  
1.  <span data-ttu-id="2206a-104">**Data Quality Client**를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-104">Launch **Data Quality Client**.</span></span> <span data-ttu-id="2206a-105">**시작**을 클릭 하 고 **모든 프로그램**을 가리킨 다음 **Microsoft SQL Server 2012**를 클릭 하 고 **Data Quality Services**를 클릭 한 다음 **Data Quality Client**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-105">Click **Start**, point to **All Programs**, click **Microsoft SQL Server 2012**, click **Data Quality Services**, and then click **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="2206a-106">**서버에 연결** 대화 상자에서 DQS가 설치 된 데이터베이스 서버 인스턴스를 선택 하 고 **연결**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-106">In the **Connect to Server** dialog box, select the database server instance on which the DQS is installed, and click **Connect**.</span></span>  
  
     <span data-ttu-id="2206a-107">![서버에 연결 대화 상자](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "서버에 연결 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="2206a-107">![Connect to Server Dialog Box](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-01.jpg "Connect to Server Dialog Box")</span></span>  
  
3.  <span data-ttu-id="2206a-108">Data Quality Client 홈 페이지의 **기술 자료 관리** 창에서 **새 기술 자료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-108">In the Data Quality Client home page, in the **Knowledge Base Management** pane, click **New Knowledge Base**.</span></span>  
  
     <span data-ttu-id="2206a-109">![기술 자료 관리 - 새 KB](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "기술 자료 관리 - 새 KB")</span><span class="sxs-lookup"><span data-stu-id="2206a-109">![Knowledge Base Management - New KB](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-02.jpg "Knowledge Base Management - New KB")</span></span>  
  
4.  <span data-ttu-id="2206a-110">기술 자료의 **이름** 으로 **Suppliers** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-110">Enter **Suppliers** for **Name** of the knowledge base.</span></span>  
  
     <span data-ttu-id="2206a-111">![새 기술 자료 - 도메인 관리](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "새 기술 자료 - 도메인 관리")</span><span class="sxs-lookup"><span data-stu-id="2206a-111">![New Knowledge Base - Domain Management](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-03.jpg "New Knowledge Base - Domain Management")</span></span>  
  
5.  <span data-ttu-id="2206a-112">**Suppliers** 기술 자료를 처음부터 만들기 때문에 **기술 자료 만들기** 필드가 **없음** 으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-112">Confirm that **Create Knowledge Base from** field is set to **None** since you are creating the **Suppliers** knowledge base from scratch.</span></span>  
  
6.  <span data-ttu-id="2206a-113">**활동** 에 대해 **도메인 관리** 가 선택 되어 있는지 확인 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-113">Confirm that **Domain Management** is selected for the **Activity** and click **Next**.</span></span> <span data-ttu-id="2206a-114">도메인 관리 작업에서는 기술 자료에 도메인을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-114">The Domain Management activity lets you create and manage domains in the knowledge base.</span></span>  
  
7.  <span data-ttu-id="2206a-115">도메인 **관리** 창 **에서 도메인 만들기 도구 모음** 단추를 클릭 하 여 도메인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-115">In the **Domain Management** window, click **Create a domain** toolbar button to create a domain.</span></span>  
  
     <span data-ttu-id="2206a-116">![도메인 만들기 도구 모음 단추](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "도메인 만들기 도구 모음 단추")</span><span class="sxs-lookup"><span data-stu-id="2206a-116">![Create Domain Toolbar Button](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-04.jpg "Create Domain Toolbar Button")</span></span>  
  
8.  <span data-ttu-id="2206a-117">**도메인 만들기** 대화 상자에서 **도메인 이름**에 대 한 **공급자 ID** 를 입력 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-117">In the **Create Domain** dialog box, type **Supplier ID** for the **Domain Name**, and click **OK**.</span></span>  
  
     <span data-ttu-id="2206a-118">![도메인 만들기 대화 상자](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "도메인 만들기 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="2206a-118">![Create Domain Dialog Box](../../2014/tutorials/media/et-creatingaknowledgebaseanddomains-05.jpg "Create Domain Dialog Box")</span></span>  
  
9. <span data-ttu-id="2206a-119">이전 단계를 반복해서 다음 도메인을 모두 기본 설정으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-119">Repeat previous step to create the following domains with all the default settings.</span></span> <span data-ttu-id="2206a-120">자습서를 간단 하 게 유지 하려면 모든 도메인의 **데이터 형식을** **문자열로**설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-120">To keep the tutorial simple, you set the **Data Type** of all the domains as **String**.</span></span> <span data-ttu-id="2206a-121">허용되는 다른 데이터 형식은 Integer, Decimal 및 Date입니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-121">The other allowed data types are: Integer, Decimal, and Date.</span></span> <span data-ttu-id="2206a-122">**선행 값 사용** 옵션을 선택 하면 (기본값) 모든 동의어가 출력에서 동의어 그룹의 선행 값으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-122">When the **Use Leading Values** option is selected (default), all synonyms are replaced with the leading value of the synonym group in the output.</span></span> <span data-ttu-id="2206a-123">**문자열 정규화** 옵션 (기본값)을 설정 하면 도메인 값에서 모든 특수 문자를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-123">Setting **Normalize String** option (default) removes any special characters in the domain values.</span></span> <span data-ttu-id="2206a-124">**출력 형식** 옵션을 사용 하 여 도메인의 데이터 값이 출력 될 때 적용 되는 서식을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-124">The **Format Output to** option lets you select the formatting that is applied when the data values in the domain are output.</span></span> <span data-ttu-id="2206a-125">도메인을 채울 때 모든 문자열 값에 대해 맞춤법 검사기를 실행 하려면 **맞춤법 검사기 사용** (기본값)을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-125">Select **Enable Speller** (default) to run Speller on all string values when populating the domain.</span></span> <span data-ttu-id="2206a-126">**언어** 설정은 적용 하려는 **맞춤법 검사기** 의 언어 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-126">The **Language** setting specifies which language version of the **Speller** you want to apply.</span></span> <span data-ttu-id="2206a-127">구문 오류에 대 한 문자열 값을 검사 하지 않고 도메인을 채우려면 **구문 오류 알고리즘 사용 안 함** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2206a-127">Select **Disable Syntax Error Algorithms** to populate the domain without checking string values for syntax errors.</span></span> <span data-ttu-id="2206a-128">자세한 내용은 MSDN 라이브러리에서 [도메인 만들기](https://msdn.microsoft.com/library/hh510401.aspx) 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2206a-128">See [Create a Domain](https://msdn.microsoft.com/library/hh510401.aspx) topic in the MSDN library for more details.</span></span>  
  
    -   <span data-ttu-id="2206a-129">Supplier Name</span><span class="sxs-lookup"><span data-stu-id="2206a-129">Supplier Name</span></span>  
  
    -   <span data-ttu-id="2206a-130">담당자 이메일</span><span class="sxs-lookup"><span data-stu-id="2206a-130">Contact Email</span></span>  
  
    -   <span data-ttu-id="2206a-131">Address Line</span><span class="sxs-lookup"><span data-stu-id="2206a-131">Address Line</span></span>  
  
    -   <span data-ttu-id="2206a-132">도시</span><span class="sxs-lookup"><span data-stu-id="2206a-132">City</span></span>  
  
    -   <span data-ttu-id="2206a-133">주</span><span class="sxs-lookup"><span data-stu-id="2206a-133">State</span></span>  
  
    -   <span data-ttu-id="2206a-134">국가</span><span class="sxs-lookup"><span data-stu-id="2206a-134">Country</span></span>  
  
    -   <span data-ttu-id="2206a-135">Zip</span><span class="sxs-lookup"><span data-stu-id="2206a-135">Zip</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="2206a-136">다음 단계</span><span class="sxs-lookup"><span data-stu-id="2206a-136">Next Step</span></span>  
 [<span data-ttu-id="2206a-137">태스크 2: 도메인 값을 수동으로 추가</span><span class="sxs-lookup"><span data-stu-id="2206a-137">Task 2: Adding Domain Values Manually</span></span>](../../2014/tutorials/task-2-adding-domain-values-manually.md)  
  
  
