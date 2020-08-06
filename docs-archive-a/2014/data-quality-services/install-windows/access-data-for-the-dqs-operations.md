---
title: DQS 작업을 위해 데이터 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 88dfb9ea-6321-4eaf-b9e4-45d36ef048f6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 515b087a8d16e44314d1a21d3dfbd6f13c767f5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733200"
---
# <a name="access-data-for-the-dqs-operations"></a><span data-ttu-id="66ab8-102">DQS 작업을 위해 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="66ab8-102">Access Data for the DQS Operations</span></span>
  <span data-ttu-id="66ab8-103">[!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 작업에 원본 데이터를 사용하고 처리된 데이터를 내보내려면 다음 중 하나를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-103">To use your source data for [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) operations, and export your processed data, you can do either of the following:</span></span>  
  
-   <span data-ttu-id="66ab8-104">원본 데이터를 DQS_STAGING_DATA 데이터베이스의 테이블/뷰로 복사한 다음 이를 DQS 작업에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-104">Copy your source data to a table/view in the DQS_STAGING_DATA database, and then use it for DQS operations.</span></span> <span data-ttu-id="66ab8-105">처리된 데이터를 DQS_STAGING_DATA 데이터베이스의 새 테이블로 내보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-105">You can also export the processed data to a new table in the DQS_STAGING_DATA database.</span></span> <span data-ttu-id="66ab8-106">이렇게 하려면 Windows 사용자 계정에 DQS_STAGING_DATA 데이터베이스에 대한 읽기/쓰기 액세스 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-106">To do so, your Windows user account must be granted read/write access to the DQS_STAGING_DATA database.</span></span>  
  
-   <span data-ttu-id="66ab8-107">사용자 데이터베이스를 DQS 작업의 원본 데이터 및 처리된 데이터의 내보내기 대상으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-107">Use your own database as the source data for the DQS operations, and destination for exporting the processed data.</span></span> <span data-ttu-id="66ab8-108">이렇게 하려면 사용자 데이터베이스가 데이터 품질 서버 데이터베이스와 동일한 SQL Server 인스턴스에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-108">To do so, ensure that your database is in the same SQL Server instance as the Data Quality Server databases.</span></span> <span data-ttu-id="66ab8-109">그렇지 않으면 데이터 품질 클라이언트에서 해당 데이터베이스를 DQS 작업에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-109">Otherwise, the database will not be available in the Data Quality Client for DQS operations.</span></span> <span data-ttu-id="66ab8-110">또한 일치하는 결과는 2단계로 내보내지므로 일치하는 결과를 내보내려면 Windows 사용자 계정에 DQS_STAGING_DATA 데이터베이스에 대한 읽기 권한을 부여해야 합니다. 먼저 일치하는 결과를 DQS_STAGING_DATA 데이터베이스의 임시 표로 내보낸 다음 대상 데이터베이스의 표로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-110">Also, your Windows user account must be granted access on the DQS_STAGING_DATA database for exporting the matching results because matching results are exported in two phases: first, the matching results are exported to the temporary tables in the DQS_STAGING_DATA database, and then moved to the table in your destination database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="66ab8-111">전제 조건</span><span class="sxs-lookup"><span data-stu-id="66ab8-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="66ab8-112">DQSInstaller.exe 파일을 실행하여 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 설치를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-112">You must have completed the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="66ab8-113">자세한 내용은 [DQSInstaller.exe를 실행하여 Data Quality 서버 설치 완료](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="66ab8-113">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
-   <span data-ttu-id="66ab8-114">데이터베이스에서 SQL 로그인에 대한 액세스 권한을 부여/수정하려면 Windows 사용자 계정은 데이터베이스 엔진 인스턴스에서 적절한 고정 서버 역할(예: securityadmin, serveradmin 또는 sysadmin)의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-114">Your Windows user account must be a member of the appropriate fixed server role (such as securityadmin, serveradmin, or sysadmin) in the database engine instance to grant/modify access to SQL login on databases.</span></span>  
  
### <a name="to-grant-readwrite-access-to-a-user-on-the-dqs_staging_data-database"></a><span data-ttu-id="66ab8-115">사용자에게 DQS_STAGING_DATA 데이터베이스에 대한 읽기/쓰기 액세스 권한을 부여하려면</span><span class="sxs-lookup"><span data-stu-id="66ab8-115">To grant read/write access to a User on the DQS_STAGING_DATA Database</span></span>  
  
1.  <span data-ttu-id="66ab8-116">Microsoft SQL Server Management Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-116">Start Microsoft SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="66ab8-117">Microsoft SQL Server Management Studio에서 해당 SQL Server 인스턴스를 확장하고 **보안**을 확장한 다음 **로그인**을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-117">In Microsoft SQL Server Management Studio, expand your SQL Server instance, and expand **Security**, and then expand **Logins**.</span></span>  
  
3.  <span data-ttu-id="66ab8-118">SQL 로그인을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-118">Right-click a SQL login, and click **Properties**.</span></span>  
  
4.  <span data-ttu-id="66ab8-119">**로그인 속성** 대화 상자의 왼쪽 창에서 **사용자 매핑** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-119">In the **Login Properties** dialog box, click the **User Mapping** page in the left pane.</span></span>  
  
5.  <span data-ttu-id="66ab8-120">오른쪽 창에서 **DQS_STAGING_DATA** 데이터베이스에 대한 **매핑** 열 아래의 확인란을 선택한 후 **데이터베이스 역할 멤버 자격: DQS_STAGING_DATA** 창에서 다음 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-120">In the right pane, select the check box under the **Map** column for the **DQS_STAGING_DATA** database, and then select the following roles in the **Database role membership for: DQS_STAGING_DATA** pane:</span></span>  
  
    -   <span data-ttu-id="66ab8-121">**db_datareader**: 테이블/뷰에서 데이터를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-121">**db_datareader**: Read data from tables/views.</span></span>  
  
    -   <span data-ttu-id="66ab8-122">**db_datawriter**: 테이블에서 데이터를 추가, 삭제 또는 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-122">**db_datawriter**: Add, delete, or change data in tables.</span></span>  
  
    -   <span data-ttu-id="66ab8-123">**db_ddladmin**: 테이블/뷰를 만들기, 수정 또는 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-123">**db_ddladmin**: Create, modify, or delete tables/views.</span></span>  
  
6.  <span data-ttu-id="66ab8-124">**로그인 속성** 대화 상자에서 **확인** 을 클릭하여 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-124">In the **Login Properties** dialog box, click **OK** to apply the changes.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="66ab8-125">다음 단계</span><span class="sxs-lookup"><span data-stu-id="66ab8-125">Next Steps</span></span>  
 <span data-ttu-id="66ab8-126">DQS 작업을 위한 데이터 원본으로 데이터베이스에 액세스하는 DQS 작업을 수행한 다음 처리된 데이터를 데이터베이스로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="66ab8-126">Try performing DQS operations that accesses the database as data source for DQS operation, and then exports the processed data to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ab8-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66ab8-127">See Also</span></span>  
 [<span data-ttu-id="66ab8-128">Data Quality Services 설치</span><span class="sxs-lookup"><span data-stu-id="66ab8-128">Install Data Quality Services</span></span>](install-data-quality-services.md)  
  
  
