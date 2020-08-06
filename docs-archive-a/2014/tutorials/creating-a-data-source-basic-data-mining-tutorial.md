---
title: 데이터 원본 만들기 (기본 데이터 마이닝 자습서) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d7107c32-69ed-49a8-9b6e-32753eebf42c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d8d5974c3685476f5d7a5751fb71bfa98384cf36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649285"
---
# <a name="creating-a-data-source-basic-data-mining-tutorial"></a><span data-ttu-id="68992-102">데이터 원본 만들기(기본 데이터 마이닝 자습서)</span><span class="sxs-lookup"><span data-stu-id="68992-102">Creating a Data Source (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="68992-103">*데이터 원본은* 프로젝트에서 저장 및 관리 되 고 데이터베이스에 배포 되는 데이터 연결입니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="68992-103">A *data source* is a data connection that is saved and managed in your project and deployed to your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="68992-104">데이터 원본에는 원본 데이터가 있는 서버 및 데이터베이스의 이름뿐만 아니라 필요한 기타 연결 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="68992-104">The data source contains the names of the server and database where your source data resides, in addition to any other required connection properties.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="68992-105">데이터베이스의 이름은 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]입니다.</span><span class="sxs-lookup"><span data-stu-id="68992-105">The name of the database is [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span> <span data-ttu-id="68992-106">이 데이터베이스를 아직 설치 하지 않은 경우 [MICROSOFT SQL 예제 데이터베이스](https://go.microsoft.com/fwlink/?LinkId=88417) 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="68992-106">If you have not already installed this database, see the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page.</span></span>  
  
### <a name="to-create-a-data-source"></a><span data-ttu-id="68992-107">데이터 원본을 만들려면</span><span class="sxs-lookup"><span data-stu-id="68992-107">To create a data source</span></span>  
  
1.  <span data-ttu-id="68992-108">**솔루션 탐색기**에서 **데이터 원본** 폴더를 마우스 오른쪽 단추로 클릭 하 고 **새 데이터 원본**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-108">In **Solution Explorer**, right-click the **Data Sources** folder and select **New Data Source**.</span></span>  
  
2.  <span data-ttu-id="68992-109">**데이터 원본 마법사 시작** 페이지에서 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-109">On the **Welcome to the Data Source Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="68992-110">**연결 정의 방법 선택** 페이지에서 **새로 만들기** 를 클릭 하 여 데이터베이스에 대 한 연결을 추가 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-110">On the **Select how to define the connection** page, click **New** to add a connection to the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
4.  <span data-ttu-id="68992-111">**연결 관리자**의 **공급자** 목록에서 **네이티브 OLE Db\sql Server native Client 11.0**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-111">In the **Provider** list in **Connection Manager**, select **Native OLE DB\SQL Server Native Client 11.0**.</span></span>  
  
5.  <span data-ttu-id="68992-112">**서버 이름** 상자에를 설치한 서버의 이름을 입력 하거나 선택 합니다 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="68992-112">In the **Server name** box, type or select the name of the server on which you installed [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)].</span></span>  
  
     <span data-ttu-id="68992-113">예를 들어 데이터베이스가 로컬 서버에서 호스트 되는 경우 **localhost** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-113">For example, type **localhost** if the database is hosted on the local server.</span></span>  
  
6.  <span data-ttu-id="68992-114">서버에 **로그온** 그룹에서 **Windows 인증 사용**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-114">In the **Log onto the server** group, select **Use Windows Authentication**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="68992-115">가능하면 구현자가 SQL Server 인증보다 더 안전한 인증 방법을 제공하는 Windows 인증을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-115">Whenever possible, implementers should use Windows Authentication, as it provides a more secure authentication method than SQL Server Authentication.</span></span> <span data-ttu-id="68992-116">그러나 SQL Server 인증은 이전 버전과의 호환성을 위해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="68992-116">However, SQL Server Authentication is provided for backward compatibility.</span></span> <span data-ttu-id="68992-117">인증 방법에 대 한 자세한 내용은 [데이터베이스 엔진 구성-계정 프로 비전](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="68992-117">For more information about authentication methods, see [Database Engine Configuration - Account Provisioning](../../2014/sql-server/install/database-engine-configuration-account-provisioning.md).</span></span>  
  
7.  <span data-ttu-id="68992-118">**데이터베이스 이름 선택 또는 입력** 목록에서를 선택 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 하 고 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-118">In the **Select or enter a database name** list, select [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="68992-119">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-119">Click **Next**.</span></span>  
  
9. <span data-ttu-id="68992-120">**가장 정보** 페이지에서 **서비스 계정 사용**을 클릭 하 고 **다음**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-120">On the **Impersonation Information** page, click **Use the service account**, and then click **Next**.</span></span>  
  
     <span data-ttu-id="68992-121">**마법사 완료** 페이지에서는 기본적으로 데이터 원본의 이름이 놀이 Works DW 2012입니다.</span><span class="sxs-lookup"><span data-stu-id="68992-121">On the **Completing the Wizard** page, notice that, by default, the data source is named Adventure Works DW 2012.</span></span>  
  
10. <span data-ttu-id="68992-122">**Finish**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="68992-122">Click **Finish**.</span></span>  
  
     <span data-ttu-id="68992-123">새 데이터 원본인 어드벤처 DW 2012는 솔루션 탐색기의 **데이터 원본** 폴더에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68992-123">The new data source, Adventure Works DW 2012, appears in the **Data Sources** folder in Solution Explorer.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="68992-124">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="68992-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="68992-125">기본 데이터 마이닝 자습서를 &#40;데이터 원본 뷰 만들기&#41;</span><span class="sxs-lookup"><span data-stu-id="68992-125">Creating a Data Source View &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-data-source-view-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="68992-126">단원의 이전 태스크</span><span class="sxs-lookup"><span data-stu-id="68992-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="68992-127">기본 데이터 마이닝 자습서 &#40;Analysis Services 프로젝트 만들기 자습서&#41;</span><span class="sxs-lookup"><span data-stu-id="68992-127">Creating an Analysis Services Project &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="68992-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68992-128">See Also</span></span>  
 <span data-ttu-id="68992-129">[SSAS 다차원&#41;&#40;데이터 원본 만들기](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span><span class="sxs-lookup"><span data-stu-id="68992-129">[Create a Data Source &#40;SSAS Multidimensional&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/create-a-data-source-ssas-multidimensional) </span></span>  
 <span data-ttu-id="68992-130">[데이터 원본 정의](../analysis-services/lesson-1-2-defining-a-data-source.md) </span><span class="sxs-lookup"><span data-stu-id="68992-130">[Defining a Data Source](../analysis-services/lesson-1-2-defining-a-data-source.md) </span></span>  
 [<span data-ttu-id="68992-131">가장 옵션 설정&#40;SSAS - 다차원&#41;</span><span class="sxs-lookup"><span data-stu-id="68992-131">Set Impersonation Options &#40;SSAS - Multidimensional&#41;</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional)  
  
  
