---
title: 데이터에 연결하는 다른 방법(보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: aebc5f3d-97d5-4d54-b525-753fed073a9a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2be693469318172b2a55fbcb17b33e1deaaed3df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647540"
---
# <a name="alternative-ways-to-get-a-data-connection-report-builder"></a><span data-ttu-id="8e120-102">데이터에 연결하는 다른 방법(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="8e120-102">Alternative Ways to Get a Data Connection (Report Builder)</span></span>
  <span data-ttu-id="8e120-103">데이터 연결은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스와 같은 외부 데이터 원본에 연결하는 데 필요한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-103">A data connection contains the information to connect to an external data source such as a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="8e120-104">일반적으로 데이터 원본 소유자로부터 사용할 자격 증명 유형과 연결 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-104">Usually, you get the connection information and the type of credentials to use from the data source owner.</span></span>  
  
 <span data-ttu-id="8e120-105">데이터 연결을 지정하기 위해 보고서 서버의 공유 데이터 원본을 사용하거나 특정 보고서에만 사용되는 포함된 데이터 원본을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-105">To specify a data connection, you can use a shared data source from the report server or create an embedded data source that is used only in a specific report.</span></span>  
  
 <span data-ttu-id="8e120-106">대부분의 자습서에서 포함된 데이터 원본을 사용하지만 공유 데이터 원본에 액세스할 수 있는 경우 공유 데이터 원본을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-106">In most tutorials you use embedded data sources, but if you have access to shared data sources, then you can use them instead.</span></span>  
  
## <a name="getting-a-data-connection-from-a-shared-data-source"></a><span data-ttu-id="8e120-107">공유 데이터 원본에서 데이터 연결 가져오기</span><span class="sxs-lookup"><span data-stu-id="8e120-107">Getting a Data Connection From a Shared Data Source</span></span>  
 <span data-ttu-id="8e120-108">보고서 서버에 사용할 권한이 있는 사용 가능한 공유 데이터 원본이 있는 경우 포함된 데이터 원본 대신 이 데이터 원본을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-108">If the report server has available shared data source that you have permissions to use, you can use them instead of an embedded data source.</span></span> <span data-ttu-id="8e120-109">다음 절차에서는 공유 데이터 원본을 찾고 이 원본을 사용하는 데 필요한 자격 증명을 제공하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-109">The following procedures tell how to locate the shared data sources and provide any credentials needed to use them.</span></span>  
  
 <span data-ttu-id="8e120-110">공유 데이터 원본을 사용하려면 보고서 서버를 찾아 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-110">To use a shared data source, you must browse to a report server and select one.</span></span> <span data-ttu-id="8e120-111">일반적으로 보고서 서버 관리자가 보고서 서버 URL을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-111">Usually, you get the report server URL from the report server administrator.</span></span>  
  
#### <a name="to-specify-a-data-connection-from-a-list-of-shared-data-sources"></a><span data-ttu-id="8e120-112">공유 데이터 원본 목록을 사용하여 데이터 연결을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="8e120-112">To specify a data connection from a list of shared data sources</span></span>  
  
1.  <span data-ttu-id="8e120-113">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 선택한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-113">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="8e120-114">**데이터 원본에 대한 연결 선택** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-114">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="8e120-115">데이터 원본 목록에서 액세스할 권한이 있는 데이터 원본을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-115">From the list of data sources, select a data source that you have permission to access.</span></span>  
  
3.  <span data-ttu-id="8e120-116">데이터 원본에 연결할 수 있는지 확인하려면 **연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-116">To verify that you can connect to the data source, click **Test Connection**.</span></span> <span data-ttu-id="8e120-117">"연결되었습니다."라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-117">The message "Connection created successfully" appears.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  <span data-ttu-id="8e120-118">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-118">Click **Next**.</span></span>  
  
     <span data-ttu-id="8e120-119">필요한 경우 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-119">If necessary, enter your credentials.</span></span> <span data-ttu-id="8e120-120">자격 증명을 로컬로 저장하려면 **연결과 함께 암호 저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-120">To save the credentials locally, select **Save password with connection**.</span></span> <span data-ttu-id="8e120-121">이 옵션을 선택하지 않으면 보고서를 실행할 때마다 자격 증명을 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-121">If you not select this option, you will be prompted for credentials every time that you run the report</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-specify-a-data-connection-by-browsing-to-a-shared-data-source-on-a-report-server"></a><span data-ttu-id="8e120-122">보고서 서버에서 공유 데이터 원본을 찾아 데이터 연결을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="8e120-122">To specify a data connection by browsing to a shared data source on a report server</span></span>  
  
1.  <span data-ttu-id="8e120-123">**데이터 세트 선택** 페이지에서 **데이터 세트 만들기**를 선택한 후, **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-123">On the **Choose a dataset** page, select **Create a dataset**, and then click **Next**.</span></span> <span data-ttu-id="8e120-124">**데이터 원본에 대한 연결 선택** 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-124">The **Choose a connection to a data source** page opens.</span></span>  
  
2.  <span data-ttu-id="8e120-125">**찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-125">Click **Browse**.</span></span> <span data-ttu-id="8e120-126">**데이터 원본 선택** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-126">The **Select Data Source** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="8e120-127">**찾는 위치** 드롭다운 목록에서 **최근에 사용한 사이트 및 서버**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-127">From the **Look in** drop-down list, select **Recent Sites and Servers**.</span></span> <span data-ttu-id="8e120-128">데이터 원본 창에서 서버의 URL을 클릭한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-128">In the data source pane, click the URL for your server, and then click **Open**.</span></span>  
  
     <span data-ttu-id="8e120-129">데이터 원본 또는 모델 목록이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-129">The list of data sources or models appears.</span></span>  
  
4.  <span data-ttu-id="8e120-130">또는 **이름**에 보고서 서버의 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-130">Alternatively, in **Name**, type the URL to the report server.</span></span> <span data-ttu-id="8e120-131">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-131">Click **Open**.</span></span>  
  
     <span data-ttu-id="8e120-132">보고서 작성기가 보고서 서버에 연결하고 루트 폴더에서 사용할 수 있는 데이터 원본을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-132">Report Builder connects to the report server and loads the data sources that are available at the root folder.</span></span>  
  
5.  <span data-ttu-id="8e120-133">연결할 수 있는 권한이 있는 데이터 원본이 포함된 폴더로 이동하고 데이터 원본을 선택한 다음 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-133">Navigate to a folder that contains a data source that you have sufficient permissions to connect to, select the data source, and then click **Open**.</span></span>  
  
     <span data-ttu-id="8e120-134">**데이터 원본에 대한 연결 선택** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-134">You are back on the **Choose a connection to a data source** page.</span></span>  
  
6.  <span data-ttu-id="8e120-135">데이터 원본에 연결할 수 있는지 확인하려면 **연결 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-135">To verify that you can connect to the data source, click **Test Connection**.</span></span>  
  
     <span data-ttu-id="8e120-136">"연결되었습니다."라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-136">The message "Connection created successfully" appears.</span></span> [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  <span data-ttu-id="8e120-137">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-137">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="8e120-138">사용자 이름과 암호를 입력하라는 메시지가 표시되면 자격 증명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-138">If you are prompted for a user name and password, enter your credentials.</span></span> <span data-ttu-id="8e120-139">자격 증명을 로컬로 저장하려면 **연결과 함께 암호 저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8e120-139">To save the credentials locally, select **Save password with connection**.</span></span>  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e120-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e120-140">See Also</span></span>  
 <span data-ttu-id="8e120-141">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8e120-141">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="8e120-142">자습서 &#40;보고서 작성기&#41;</span><span class="sxs-lookup"><span data-stu-id="8e120-142">Tutorials &#40;Report Builder&#41;</span></span>](report-builder-tutorials.md)  
  
  
