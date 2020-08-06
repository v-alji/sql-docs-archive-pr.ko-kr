---
title: 유틸리티 제어 지점 데이터 웨어하우스 구성(SQL Server 유틸리티) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60b9623b468f2763cf619c325412373e3603f3a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647687"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a><span data-ttu-id="435c6-102">유틸리티 제어 지점 데이터 웨어하우스 구성(SQL Server 유틸리티)</span><span class="sxs-lookup"><span data-stu-id="435c6-102">Configure Your Utility Control Point Data Warehouse (SQL Server Utility)</span></span>
  <span data-ttu-id="435c6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 관리되는 인스턴스에서 수집된 데이터는 UMDW(유틸리티 관리 데이터 웨어하우스)에 저장됩니다. UMDW의 파일 이름은 sysutility_mdw입니다.</span><span class="sxs-lookup"><span data-stu-id="435c6-103">Data collected by managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are stored in the utility management data warehouse (UMDW); the UMDW file name is sysutility_mdw.</span></span>  
  
 <span data-ttu-id="435c6-104">UMDW 데이터 보존 기간을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="435c6-104">You can configure the UMDW data retention period.</span></span> <span data-ttu-id="435c6-105">자세한 내용은 [유틸리티 관리&#40;SQL Server 유틸리티&#41;](../../database-engine/utility-administration-sql-server-utility.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="435c6-105">For more information, see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="435c6-106">다음 구성 설정은 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]릴리스에서 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="435c6-106">The following configuration settings are not configurable in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="435c6-107">UMDW 이름: Sysutility_mdw</span><span class="sxs-lookup"><span data-stu-id="435c6-107">UMDW name: Sysutility_mdw.</span></span>  
  
-   <span data-ttu-id="435c6-108">컬렉션 집합 업로드 빈도: 15분마다</span><span class="sxs-lookup"><span data-stu-id="435c6-108">Collection set upload frequency: Every 15 minutes.</span></span>  
  
 <span data-ttu-id="435c6-109">UMDW 디렉터리는 구성할 수 있으며 \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\입니다. 여기서 \<System drive>는 일반적으로 C:\ 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="435c6-109">The UMDW directory is configurable: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="435c6-110">로그 파일 Sysutility_mdw_\<GUID>_LOG는 같은 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="435c6-110">The log file, Sysutility_mdw_\<GUID>_LOG, is located in the same directory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="435c6-111">UMDW(sysutility_mdw) 파일 위치는 detach/attach 또는 ALTER DATABASE를 사용하여 변경할 수 있으며</span><span class="sxs-lookup"><span data-stu-id="435c6-111">The UMDW (sysutility_mdw) file location can be changed using detach/attach or ALTER DATABASE.</span></span> <span data-ttu-id="435c6-112">ALTER DATABASE를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="435c6-112">We recommend the use of ALTER DATABASE.</span></span> <span data-ttu-id="435c6-113">자세한 내용은 [ALTER DATABASE&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="435c6-113">For more information see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="435c6-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="435c6-114">See Also</span></span>  
 [<span data-ttu-id="435c6-115">SQL Server 유틸리티 기능 및 태스크</span><span class="sxs-lookup"><span data-stu-id="435c6-115">SQL Server Utility Features and Tasks</span></span>](sql-server-utility-features-and-tasks.md)  
  
  
