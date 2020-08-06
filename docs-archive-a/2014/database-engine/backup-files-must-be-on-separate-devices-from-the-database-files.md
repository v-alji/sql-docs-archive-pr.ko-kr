---
title: 백업 파일은 데이터베이스 파일에서 별도의 장치에 있어야 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7039bebb-1f25-4cf3-81f1-393dfb78da12
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d5eff9cb3139e1e1043f99ba63d11160b1010c27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733140"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a><span data-ttu-id="0cf89-102">백업 파일을 데이터베이스 파일과 별개의 디바이스에 두어야 함</span><span class="sxs-lookup"><span data-stu-id="0cf89-102">Backup Files Must Be on Separate Devices from the Database Files</span></span>
  <span data-ttu-id="0cf89-103">이 규칙은 데이터베이스 파일이 백업 파일과 별개의 디바이스에 있는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="0cf89-103">This rule checks whether database files are on devices separate from the backup files.</span></span> <span data-ttu-id="0cf89-104">데이터베이스 파일과 백업 파일이 동일한 디바이스에 있는 경우 해당 디바이스에 오류가 발생하면 데이터베이스와 백업을 모두 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cf89-104">If database files and backup files are on the same device and the device fails, the database and backups will be unavailable.</span></span> <span data-ttu-id="0cf89-105">또한 데이터베이스 파일과 백업 파일을 별개의 디바이스에 두면 데이터베이스의 프로덕션 사용과 백업 작성에 대한 I/O 성능이 모두 최적화됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cf89-105">Also, putting the database and backup files on the separate devices optimizes the I/O performance for both the production use of the database and the writing of backups.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="0cf89-106">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="0cf89-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="0cf89-107">데이터베이스와 백업은 별개의 백업 디바이스에 두는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0cf89-107">We strongly recommend that you put the database and backups on separate backup devices.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0cf89-108">이 정책은 탑재 지점을 통해 개별 물리적 디바이스를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0cf89-108">This policy cannot detect separate physical devices through mount points.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="0cf89-109">참조 항목</span><span class="sxs-lookup"><span data-stu-id="0cf89-109">For More Information</span></span>  
 [<span data-ttu-id="0cf89-110">백업 디바이스&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0cf89-110">Backup Devices &#40;SQL Server&#41;</span></span>](../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
 [<span data-ttu-id="0cf89-111">SQL Server 데이터베이스 백업 및 복원</span><span class="sxs-lookup"><span data-stu-id="0cf89-111">Back Up and Restore of SQL Server Databases</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
## <a name="see-also"></a><span data-ttu-id="0cf89-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0cf89-112">See Also</span></span>  
 [<span data-ttu-id="0cf89-113">정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용</span><span class="sxs-lookup"><span data-stu-id="0cf89-113">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
