---
title: 데이터와 로그 파일을 별개의 드라이브에 배치 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d3f972ea29322a046c09657e2ed2499655c82aed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652765"
---
# <a name="place-data-and-log-files-on-separate-drives"></a><span data-ttu-id="bea34-102">데이터와 로그 파일을 별개의 드라이브에 배치</span><span class="sxs-lookup"><span data-stu-id="bea34-102">Place Data and Log Files on Separate Drives</span></span>
  <span data-ttu-id="bea34-103">이 규칙은 데이터와 로그 파일이 별개의 논리적 드라이브에 배치되어 있는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="bea34-103">This rule checks whether data and log files are placed on separate logical drives.</span></span> <span data-ttu-id="bea34-104">데이터와 로그 파일을 동일 디바이스에 배치할 경우 디바이스에 경합이 발생하여 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bea34-104">Placing both data and log files on the same device can cause contention for that device and result in poor performance.</span></span> <span data-ttu-id="bea34-105">파일을 별개의 장치에 배치하면 데이터와 로그 파일에 대해 I/O 작업이 동시에 수행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bea34-105">Placing the files on separate drives allows the I/O activity to occur at the same time for both the data and log files.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="bea34-106">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="bea34-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="bea34-107">새 데이터베이스를 만들 때 데이터와 로그에 대해 별개의 드라이브를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bea34-107">When you create a new database, specify separate drives for the data and log.</span></span> <span data-ttu-id="bea34-108">데이터베이스를 만든 후 파일을 이동하려면 데이터베이스를 오프라인 상태로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bea34-108">To move files after the database is created, the database must be taken offline.</span></span> <span data-ttu-id="bea34-109">다음 중 한 가지 방법을 사용하여 파일을 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bea34-109">Move the files by using one of the following methods:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bea34-110">이 정책은 탑재 지점을 통해 개별 물리적 디바이스를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bea34-110">This policy cannot detect separate physical devices through mount points</span></span>  
  
-   <span data-ttu-id="bea34-111">RESTORE DATABASE 문을 WITH MOVE 옵션과 함께 사용하여 백업에서 데이터베이스를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="bea34-111">Restore the database from backup by using the RESTORE DATABASE statement with the WITH MOVE option.</span></span>  
  
-   <span data-ttu-id="bea34-112">데이터와 로그 디바이스에 대해 별개의 위치를 지정하여 데이터베이스를 분리하고 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bea34-112">Detach and then attach the database specifying separate locations for the data and log devices.</span></span>  
  
-   <span data-ttu-id="bea34-113">ALTER DATABASE 문을 MODIFY FILE 옵션과 함께 실행한 후 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 다시 시작하여 새 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bea34-113">Specify a new location by running the ALTER DATABASE statement with the MODIFY FILE option, and then restarting the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="bea34-114">참조 항목</span><span class="sxs-lookup"><span data-stu-id="bea34-114">For More Information</span></span>  
 [<span data-ttu-id="bea34-115">데이터베이스 파일 이동</span><span class="sxs-lookup"><span data-stu-id="bea34-115">Move Database Files</span></span>](../databases/move-database-files.md)  
  
 [<span data-ttu-id="bea34-116">사용자 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="bea34-116">Move User Databases</span></span>](../databases/move-user-databases.md)  
  
 [<span data-ttu-id="bea34-117">데이터베이스 분리 및 연결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bea34-117">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="bea34-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bea34-118">See Also</span></span>  
 [<span data-ttu-id="bea34-119">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="bea34-119">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
