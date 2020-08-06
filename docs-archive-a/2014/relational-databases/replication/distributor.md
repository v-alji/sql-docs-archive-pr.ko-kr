---
title: 배포자 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.selectdistributor.f1
ms.assetid: 787f0e9c-09dd-438a-bc04-5b8f99c127b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c601a540088b5cd9d7a2033510a5cf9b83c3170e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646907"
---
# <a name="distributor"></a><span data-ttu-id="a5d3f-102">배포자</span><span class="sxs-lookup"><span data-stu-id="a5d3f-102">Distributor</span></span>
  <span data-ttu-id="a5d3f-103">**배포자** 페이지는 배포 구성 마법사 및 새 게시 마법사에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-103">The **Distributor** page appears in the Configure Distribution Wizard and in the New Publication Wizard.</span></span> <span data-ttu-id="a5d3f-104">배포자는 배포 데이터베이스를 포함하고 모든 유형의 복제에 대한 메타데이터 및 기록 데이터를 저장하는 서버입니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-104">The Distributor is a server that contains the distribution database and stores metadata and history data for all types of replication.</span></span> <span data-ttu-id="a5d3f-105">또한 배포자는 트랜잭션 복제에 대한 트랜잭션을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-105">The Distributor also stores transactions for transactional replication.</span></span> <span data-ttu-id="a5d3f-106">배포자는 게시자와 별개인 서버(원격 배포자)가 되거나 게시자와 같은 서버(로컬 배포자)가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-106">The Distributor can be the same server as the Publisher (a local Distributor) or it can be a separate server from the Publisher (a remote Distributor).</span></span> <span data-ttu-id="a5d3f-107">배포자의 역할은 구현하는 복제의 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-107">The role of the Distributor varies, depending on which type of replication you implement.</span></span> <span data-ttu-id="a5d3f-108">일반적으로 배포자의 역할은 병합 복제 및 스냅샷 복제보다 트랜잭션 복제에서 훨씬 큽니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-108">In general, its role is much greater for transactional replication than it is for merge replication and snapshot replication.</span></span> <span data-ttu-id="a5d3f-109">보통 병합 및 스냅샷 복제에서는 로컬 배포자를 사용하지만 사용률이 매우 높은 시스템에서는 트랜잭션 배포에서 원격 배포자를 사용하는 것이 유리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-109">Merge and snapshot replication typically use a local Distributor, but transactional replication on a very busy system can benefit from using a remote Distributor.</span></span>  
  
 <span data-ttu-id="a5d3f-110">배포자가 있는 서버에는 다음과 같은 추가 리소스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-110">The Distributor uses these additional resources on the server where it is located:</span></span>  
  
-   <span data-ttu-id="a5d3f-111">게시에 대한 스냅샷 파일이 저장되어 있는 경우(일반적으로 배포자에 저장되어 있음) 추가 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="a5d3f-111">Additional disk space if the snapshot files for the publication are stored on it (which they typically are).</span></span>  
  
-   <span data-ttu-id="a5d3f-112">배포 데이터베이스를 저장할 추가 디스크 공간</span><span class="sxs-lookup"><span data-stu-id="a5d3f-112">Additional disk space to store the distribution database.</span></span>  
  
-   <span data-ttu-id="a5d3f-113">배포자에서 실행되는 밀어넣기 구독에 대해 복제 에이전트가 사용할 추가 프로세서</span><span class="sxs-lookup"><span data-stu-id="a5d3f-113">Additional processor usage by replication agents for push subscriptions running on the Distributor.</span></span>  
  
 <span data-ttu-id="a5d3f-114">배포자로 선택된 서버는 복제 및 해당 서버의 다른 작업을 지원하기 위해 충분한 디스크 공간과 처리 성능이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-114">The server you select as the Distributor should have adequate disk space and processor power to support replication and any other activities on that server.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a5d3f-115">옵션</span><span class="sxs-lookup"><span data-stu-id="a5d3f-115">Options</span></span>  
 <span data-ttu-id="a5d3f-116">**'\<ServerName>'을(를) 자체 배포자로 사용합니다. SQL Server에서 배포 데이터베이스와 로그를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="a5d3f-116">**'\<ServerName>' will act as its own Distributor; SQL Server will create a distribution database and log**</span></span>  
 <span data-ttu-id="a5d3f-117">연결된 서버를 배포자로 구성하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-117">Select this option to configure the server you are connected to as a Distributor.</span></span>  
  
 <span data-ttu-id="a5d3f-118">**다음 서버를 배포자로 사용(참고: 선택한 서버는 이미 배포자로 구성되어 있어야 함)**</span><span class="sxs-lookup"><span data-stu-id="a5d3f-118">**Use the following server as the Distributor (Note: the server you select must already be configured as a Distributor)**</span></span>  
 <span data-ttu-id="a5d3f-119">다른 서버를 배포자로 구성하려면 이 옵션을 선택하고 서버 이름을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-119">Select this option and then click on the name of a server below to configure another server as the Distributor.</span></span>  
  
 <span data-ttu-id="a5d3f-120">**추가**</span><span class="sxs-lookup"><span data-stu-id="a5d3f-120">**Add**</span></span>  
 <span data-ttu-id="a5d3f-121">배포자로 사용할 서버가 목록에 없으면 **추가** 를 클릭하여 서버를 식별하고 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-121">If the server you want to use as a Distributor is not listed, click **Add** to identify the server and add it to the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5d3f-122">원격 서버를 배포자로 사용하려면 원격 서버가 이미 배포자로 구성되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-122">To use a remote server as the Distributor, the remote server must already be configured as a Distributor.</span></span> <span data-ttu-id="a5d3f-123">이 마법사가 실행 중인 서버는 해당 배포자에서 게시자로 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5d3f-123">The server against which this wizard is running must be enabled as a Publisher on that Distributor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5d3f-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5d3f-124">See Also</span></span>  
 <span data-ttu-id="a5d3f-125">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="a5d3f-125">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="a5d3f-126">게시 및 배포 구성</span><span class="sxs-lookup"><span data-stu-id="a5d3f-126">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)  
  
  
