---
title: '2단원: 연결 정보 지정(Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c187f0abdc4b277a5f1428407b5c42ca4fd6fee6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731427"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a><span data-ttu-id="992bf-102">2단원: 연결 정보 지정(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="992bf-102">Lesson 2: Specifying Connection Information (Reporting Services)</span></span>
  <span data-ttu-id="992bf-103">Tutorial 프로젝트에 보고서를 추가한 뒤에는 보고서에서 관계형 데이터베이스, 다차원 데이터베이스 또는 다른 리소스의 데이터에 액세스하기 위해 사용하는 연결 정보인 *데이터 원본*을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-103">After you add a report to the Tutorial project, you need to define a *data source*, which is connection information the report uses to access data from either a relational database, multidimensional database, or other resource.</span></span>  
  
 <span data-ttu-id="992bf-104">이 단원에서는 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 예제 데이터베이스를 데이터 원본으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-104">In this lesson, you will use the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database as your data source.</span></span> <span data-ttu-id="992bf-105">이 자습서에서는이 데이터베이스가 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 로컬 컴퓨터에 설치 된의 기본 인스턴스에 있다고 가정 [!INCLUDE[ssDE](../includes/ssde-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-105">This tutorial assumes that this database is located in a default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] that is installed on your local computer.</span></span>  
  
### <a name="to-set-up-a-connection"></a><span data-ttu-id="992bf-106">연결을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="992bf-106">To set up a connection</span></span>  
  
1.  <span data-ttu-id="992bf-107">**보고서 데이터** 창에서 **새로 만들기** 를 클릭 한 다음 **데이터 원본 ...** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-107">In the **Report Data** pane, click **New** and then click **Data Source...**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="992bf-108">**보고서 데이터** 창이 표시되지 않는 경우 **보기** 메뉴에서 **보고서 데이터**를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="992bf-108">If the **Report Data** pane is not visible, from the **View** menu, click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="992bf-109">**이름**에서 [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)]을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-109">In **Name**, type [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)].</span></span>  
  
3.  <span data-ttu-id="992bf-110">**포함된 연결** 이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-110">Make sure **Embedded connection** is selected.</span></span>  
  
4.  <span data-ttu-id="992bf-111">**유형**에서 **Microsoft SQL Server**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-111">In **Type**, select **Microsoft SQL Server**.</span></span>  
  
5.  <span data-ttu-id="992bf-112">**연결 문자열**에서 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-112">In **Connection string**, type the following:</span></span>  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     <span data-ttu-id="992bf-113">이 연결 문자열에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], 보고서 서버 및 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스가 모두 로컬 컴퓨터에 설치되어 있고 사용자에게 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 데이터베이스에 로그온할 수 있는 권한이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-113">This connection string assumes that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the report server, and the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database are all installed on the local computer and that you have permission to log on to the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="992bf-114">[!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services 또는 명명된 인스턴스를 사용하는 경우에는 연결 문자열에 인스턴스 정보가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-114">If you are using [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services or a named instance, the connection string must include instance information:</span></span>  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  <span data-ttu-id="992bf-115">연결 문자열에 대 한 자세한 내용은 Reporting Services 및 [데이터 원본 속성 대화 상자, 일반](data-source-properties-dialog-box-general.md) [의 데이터 연결, 데이터 원본 및 연결 문자열](data-connections-data-sources-and-connection-strings-in-reporting-services.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="992bf-115">For more information about connection strings, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md) and [Data Source Properties Dialog Box, General](data-source-properties-dialog-box-general.md).</span></span>  
  
6.  <span data-ttu-id="992bf-116">왼쪽 창에서 **자격 증명** 을 클릭하고 **Windows 인증 사용(통합 보안)** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-116">Click **Credentials** in the left pane and click **Use Windows Authentication (integrated security)**.</span></span>  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="992bf-117">데이터 원본이 [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] **보고서 데이터** 창에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-117">data source [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] is added to the **Report Data** pane.</span></span>  
  
## <a name="next-task"></a><span data-ttu-id="992bf-118">다음 태스크</span><span class="sxs-lookup"><span data-stu-id="992bf-118">Next Task</span></span>  
 <span data-ttu-id="992bf-119">[!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 샘플 데이터베이스에 대한 연결이 정의되었습니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-119">You have successfully defined a connection to the [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] sample database.</span></span> <span data-ttu-id="992bf-120">다음 단원에서는 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="992bf-120">Next, you will create the report.</span></span> <span data-ttu-id="992bf-121">[3단원: 테이블 보고서에 대한 데이터 세트 정의&#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="992bf-121">See [Lesson 3: Defining a Dataset for the Table Report &#40;Reporting Services&#41;](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992bf-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="992bf-122">See Also</span></span>  
 [<span data-ttu-id="992bf-123">보고서 서비스의 데이터 연결, 데이터 원본 및 연결 문자열</span><span class="sxs-lookup"><span data-stu-id="992bf-123">Data Connections, Data Sources, and Connection Strings in Reporting Services</span></span>](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
