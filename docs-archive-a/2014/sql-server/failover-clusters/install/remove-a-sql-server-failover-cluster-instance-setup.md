---
title: SQL Server 장애 조치(Failover) 클러스터 인스턴스 제거(설치) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], removing failover clustered instance
- failover clustering [SQL Server], removing failover clustered instance
- uninstalling failover clustered instances
- removing failover clustered instances
ms.assetid: bf63353b-69cf-4c5c-98ea-7b151e36537f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a4d0ae492481b0677be2d2692fbda0fbc8eb604b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650588"
---
# <a name="remove-a-sql-server-failover-cluster-instance-setup"></a><span data-ttu-id="7ae4a-102">SQL Server 장애 조치(Failover) 클러스터 인스턴스 제거(설치)</span><span class="sxs-lookup"><span data-stu-id="7ae4a-102">Remove a SQL Server Failover Cluster Instance (Setup)</span></span>
  <span data-ttu-id="7ae4a-103">이 절차를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치 클러스터형 인스턴스를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ae4a-103">Use this procedure to uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover clustered instance.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ae4a-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터를 업데이트하거나 제거하려면 장애 조치(Failover) 클러스터의 모든 노드에 서비스로 로그인할 수 있는 권한을 가진 로컬 관리자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ae4a-104">To update or remove a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, you must be a local administrator with permission to login as a service on all nodes of the failover cluster.</span></span>  
  
 <span data-ttu-id="7ae4a-105">**시작하기 전 주의 사항**</span><span class="sxs-lookup"><span data-stu-id="7ae4a-105">**Before you begin**</span></span>  
  
 <span data-ttu-id="7ae4a-106">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터를 제거하기 전에 다음 중요 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ae4a-106">Consider the following important points before you uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster:</span></span>  
  
-   <span data-ttu-id="7ae4a-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 실수로 제거한 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 리소스가 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ae4a-107">If [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is uninstalled by accident, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resources will fail to start.</span></span> <span data-ttu-id="7ae4a-108">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client를 다시 설치하려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치 프로그램을 실행하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 필수 구성 요소를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="7ae4a-108">To reinstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, run the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup program to install [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prerequisites.</span></span>  
  
-   <span data-ttu-id="7ae4a-109">두 개 이상의 SQL IP 클러스터 리소스를 갖고 있는 장애 조치(Failover) 클러스터를 제거한 경우 클러스터 관리자를 사용하여 추가 SQL IP 리소스를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ae4a-109">If you uninstall a failover cluster that has more than one SQL IP cluster resource, you must remove the additional SQL IP resources using cluster administrator.</span></span>  
  
 <span data-ttu-id="7ae4a-110">명령 프롬프트 구문에 대 한 자세한 내용은 [명령 프롬프트에서 SQL Server 2014 설치](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7ae4a-110">For information about command prompt syntax, see [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
### <a name="to-uninstall-a-ssnoversion-failover-cluster"></a><span data-ttu-id="7ae4a-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터를 제거하려면</span><span class="sxs-lookup"><span data-stu-id="7ae4a-111">To uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster</span></span>  
  
1.  <span data-ttu-id="7ae4a-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 장애 조치(Failover) 클러스터를 제거하려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 설치 프로그램이 제공하는 노드 제거 기능을 사용하여 각 노드를 개별적으로 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="7ae4a-112">To uninstall a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, use the Remove Node functionality provided by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup to remove each node individually.</span></span> <span data-ttu-id="7ae4a-113">자세한 내용은 [SQL Server 장애 조치(failover) 클러스터에서 노드 추가 또는 제거&#40;설치 프로그램&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ae4a-113">For more information, see [Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae4a-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ae4a-114">See Also</span></span>  
 [<span data-ttu-id="7ae4a-115">SQL Server 설치 로그 파일 보기 및 읽기</span><span class="sxs-lookup"><span data-stu-id="7ae4a-115">View and Read SQL Server Setup Log Files</span></span>](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
