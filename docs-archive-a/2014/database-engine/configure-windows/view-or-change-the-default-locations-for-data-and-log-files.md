---
title: 데이터 및 로그 파일의 기본 위치 보기 또는 변경 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: def6be137aecbab7f2730fa4c2bf210b374a3a7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729788"
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files-sql-server-management-studio"></a><span data-ttu-id="6bad0-102">데이터 및 로그 파일의 기본 위치 보기 또는 변경(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6bad0-102">View or Change the Default Locations for Data and Log Files (SQL Server Management Studio)</span></span>
  <span data-ttu-id="6bad0-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 새 데이터 및 로그 파일의 기본 위치를 보고 변경하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad0-103">This topic describes how to view and change the default locations of new data and log files in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="6bad0-104">기본 경로는 레지스트리에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6bad0-104">The default path is obtained from the registry.</span></span> <span data-ttu-id="6bad0-105">위치를 변경하면 다른 위치를 지정하지 않는 한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 만들어지는 모든 새 데이터베이스가 해당 위치를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad0-105">After you change the location all new databases created in the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will use that location if a different location is not specified.</span></span>  
  
 <span data-ttu-id="6bad0-106">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="6bad0-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6bad0-107">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="6bad0-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6bad0-108">권장 사항</span><span class="sxs-lookup"><span data-stu-id="6bad0-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="6bad0-109">**데이터 및 로그 파일 기본 위치를 보거나 변경하려면:**</span><span class="sxs-lookup"><span data-stu-id="6bad0-109">**To view or change the data and log file default locations, using:**</span></span>  
  
     [<span data-ttu-id="6bad0-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6bad0-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
-   <span data-ttu-id="6bad0-111">**후속 작업:**  [기본 위치를 변경한 후](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="6bad0-111">**Follow Up:**  [Changing the Default Locations](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6bad0-112">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6bad0-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="6bad0-113">권장 사항</span><span class="sxs-lookup"><span data-stu-id="6bad0-113">Recommendations</span></span>  
 <span data-ttu-id="6bad0-114">데이터 파일 및 로그 파일을 보호하는 최선의 방법은 ACL(액세스 제어 목록)로 보호하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6bad0-114">The best practice for protecting your data files and log files is to ensure that they are protected by access control lists (ACLs).</span></span> <span data-ttu-id="6bad0-115">ACL은 파일을 만든 위치의 루트 디렉터리에 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad0-115">The ACLs should be set on the directory root under which the files are created.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6bad0-116">보안</span><span class="sxs-lookup"><span data-stu-id="6bad0-116">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6bad0-117">권한</span><span class="sxs-lookup"><span data-stu-id="6bad0-117">Permissions</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6bad0-118">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="6bad0-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-default-locations-for-database-files"></a><span data-ttu-id="6bad0-119">데이터베이스 파일의 기본 위치를 보거나 변경하려면</span><span class="sxs-lookup"><span data-stu-id="6bad0-119">To view or change the default locations for database files</span></span>  
  
1.  <span data-ttu-id="6bad0-120">개체 탐색기에서 서버를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad0-120">In Object Explorer, right-click a server and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6bad0-121">왼쪽 패널에서 **데이터베이스 설정** 페이지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad0-121">In the left panel, click the **Database settings** page.</span></span>  
  
3.  <span data-ttu-id="6bad0-122">**데이터베이스 기본 위치**에서 새 데이터 파일 및 새 로그 파일의 현재 기본 위치를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6bad0-122">In **Database default locations**, view the current default locations for new data files and new log files.</span></span> <span data-ttu-id="6bad0-123">기본 위치를 변경하려면 **데이터** 또는 **로그** 필드에 새 기본 경로 이름을 입력하거나 찾아보기 단추를 클릭한 다음 경로 이름을 찾아 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad0-123">To change a default location, enter a new default pathname in the **Data** or **Log** field, or click the browse button to find and select a pathname.</span></span>  
  
##  <a name="follow-up-after-changing-the-default-locations"></a><a name="FollowUp"></a><span data-ttu-id="6bad0-124">후속 작업: 기본 위치를 변경한 후</span><span class="sxs-lookup"><span data-stu-id="6bad0-124">Follow Up: After Changing the Default Locations</span></span>  
 <span data-ttu-id="6bad0-125">변경 내용을 적용하려면 SQL Server 서비스를 중지했다가 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bad0-125">You must stop and start the SQL Server service to complete the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bad0-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6bad0-126">See Also</span></span>  
 <span data-ttu-id="6bad0-127">[CREATE DATABASE&#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6bad0-127">[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql) </span></span>  
 [<span data-ttu-id="6bad0-128">데이터베이스 만들기</span><span class="sxs-lookup"><span data-stu-id="6bad0-128">Create a Database</span></span>](../../relational-databases/databases/create-a-database.md)  
  
  
