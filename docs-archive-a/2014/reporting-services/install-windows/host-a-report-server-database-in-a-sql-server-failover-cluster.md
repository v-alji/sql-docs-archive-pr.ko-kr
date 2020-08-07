---
title: SQL Server 장애 조치(Failover) 클러스터에서 보고서 서버 데이터베이스 호스팅 | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 921ce03fd08e7820266b828d5848f64db1e257ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732435"
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a><span data-ttu-id="c405a-102">SQL Server 장애 조치(failover) 클러스터에서 보고서 서버 데이터베이스 호스팅</span><span class="sxs-lookup"><span data-stu-id="c405a-102">Host a Report Server Database in a SQL Server Failover Cluster</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c405a-103">에서는 장애 조치 클러스터링을 지원하므로 하나 이상의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 여러 디스크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c405a-103">provides failover clustering support so that you can use multiple disks for one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances.</span></span> <span data-ttu-id="c405a-104">장애 조치 클러스터링은 보고서 서버 데이터베이스에 대해서만 지원되므로 보고서 서버 서비스를 장애 조치 클러스터의 일부로 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c405a-104">Failover clustering is supported only for the report server database; you cannot run the Report Server service as part of a failover cluster.</span></span>  
  
 <span data-ttu-id="c405a-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치 클러스터에서 보고서 서버 데이터베이스를 호스팅하려면 클러스터가 이미 설치되고 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c405a-105">To host a report server database on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, the cluster must already be installed and configured.</span></span> <span data-ttu-id="c405a-106">그러면 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 도구의 데이터베이스 설치 페이지에서 보고서 서버 데이터베이스를 만들 때 장애 조치 클러스터를 서버 이름으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c405a-106">You can then select the failover cluster as the server name when you create the report server database in the Database Setup page of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span>  
  
 <span data-ttu-id="c405a-107">보고서 서버 서비스가 장애 조치 클러스터에 참여할 수는 없지만 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 장애 조치 클러스터가 설치된 컴퓨터에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 설치할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c405a-107">Although the Report Server service cannot participate in a failover cluster, you can install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on a computer that has a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster installed.</span></span> <span data-ttu-id="c405a-108">보고서 서버는 장애 조치 클러스터와 독립적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c405a-108">The report server runs independently of the failover cluster.</span></span> <span data-ttu-id="c405a-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치 인스턴스의 일부인 컴퓨터에 보고서 서버를 설치하는 경우에는 보고서 서버 데이터에 장애 조치 클러스터를 사용하지 않아도 되므로 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 사용하여 데이터베이스를 호스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c405a-109">If you install a report server on a computer that is part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover instance, you are not required to use the failover cluster for the report server database; you can use a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c405a-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c405a-110">See Also</span></span>  
 <span data-ttu-id="c405a-111">[보고서 서버 데이터베이스&#40;SSRS 기본 모드&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="c405a-111">[Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="c405a-112">보고서 서버 데이터베이스 만들기&#40;SSRS 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="c405a-112">Create a Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
  
  
