---
title: 서버에 연결(Oracle), 연결 속성 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c76a3058283a098357701a44de48efff917acd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646372"
---
# <a name="connect-to-server-oracle-connection-properties"></a><span data-ttu-id="e313e-102">서버에 연결(Oracle), 연결 속성</span><span class="sxs-lookup"><span data-stu-id="e313e-102">Connect to Server (Oracle), Connection Properties</span></span>
  <span data-ttu-id="e313e-103">**서버에 연결** 대화 상자의 **연결 속성** 탭을 사용하여 **게이트웨이** 또는 **전체**게시 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e313e-103">Use the **Connection Properties** tab of the **Connect to Server** dialog box to specify a publishing option of **Gateway** or **Complete**.</span></span> <span data-ttu-id="e313e-104">게시자를 식별한 다음에 이 옵션을 변경하려면 해당 게시자를 삭제하고 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e313e-104">After a Publisher is identified, this option cannot be changed without dropping and reconfiguring the Publisher.</span></span> <span data-ttu-id="e313e-105">자세한 내용은 [Oracle 게시자 구성](non-sql/configure-an-oracle-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e313e-105">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e313e-106">옵션</span><span class="sxs-lookup"><span data-stu-id="e313e-106">Options</span></span>  
 <span data-ttu-id="e313e-107">**게시자 유형**</span><span class="sxs-lookup"><span data-stu-id="e313e-107">**Publisher type**</span></span>  
 <span data-ttu-id="e313e-108">**게이트웨이** 또는 **전체**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e313e-108">Select **Gateway** or **Complete**.</span></span> <span data-ttu-id="e313e-109">**전체** 옵션은 Oracle 게시에 대해 지원되는 완전한 기능 집합을 스냅샷 및 트랜잭션 게시에 제공하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e313e-109">The **Complete** option is designed to provide snapshot and transactional publications with the complete set of supported features for Oracle publishing.</span></span> <span data-ttu-id="e313e-110">**게이트웨이** 옵션은 복제가 시스템 간의 게이트웨이로 사용되는 경우 성능을 향상시킬 수 있도록 특정 디자인 최적화를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e313e-110">The **Gateway** option provides specific design optimizations to improve performance for cases where replication serves as a gateway between systems.</span></span> <span data-ttu-id="e313e-111">동일한 테이블을 여러 트랜잭션 게시에 게시하려는 경우에는 **게이트웨이** 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e313e-111">The **Gateway** option cannot be used if you plan to publish the same table in multiple transactional publications.</span></span> <span data-ttu-id="e313e-112">**게이트웨이**를 선택하면 트랜잭션 게시의 경우 특정 테이블이 한 번만 나타날 수 있지만 스냅샷 게시의 경우에는 이러한 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e313e-112">A table can appear in at most one transactional publication and any number of snapshot publications if you select **Gateway**.</span></span>  
  
 <span data-ttu-id="e313e-113">**제한 시간**</span><span class="sxs-lookup"><span data-stu-id="e313e-113">**Timeouts**</span></span>  
 <span data-ttu-id="e313e-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 배포자가 제한 시간 오류가 발생할 때까지 Oracle 게시자에 연결을 시도하는 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e313e-114">Specify how long the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor should attempt to connect to the Oracle Publisher before a timeout error occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e313e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e313e-115">See Also</span></span>  
 <span data-ttu-id="e313e-116">[Oracle 게시를 위한 용어 설명](non-sql/glossary-of-terms-for-oracle-publishing.md) </span><span class="sxs-lookup"><span data-stu-id="e313e-116">[Glossary of Terms for Oracle Publishing](non-sql/glossary-of-terms-for-oracle-publishing.md) </span></span>  
 [<span data-ttu-id="e313e-117">Oracle 게시자를 위한 성능 튜닝</span><span class="sxs-lookup"><span data-stu-id="e313e-117">Performance Tuning for Oracle Publishers</span></span>](non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
