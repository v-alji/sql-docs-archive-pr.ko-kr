---
title: SQL Server 이외 구독자 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], non-SQL Server Subscribers
- heterogeneous data sources, non-SQL Server Subscribers
- heterogeneous data sources
- heterogeneous database replication, non-SQL Server Subscribers
- non-SQL Server Subscribers, about non-SQL Server Subscribers
- heterogeneous Subscribers
- heterogeneous Subscribers, about heterogeneous Subscribers
- Subscribers [SQL Server replication], non-SQL Server Subscribers
- non-SQL Server Subscribers
ms.assetid: 831e7586-2949-4b9b-a2f3-7b0b699b23ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a42ba5aedff4f23c6fb6be4155b1c6d4bf20471
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733920"
---
# <a name="non-sql-server-subscribers"></a><span data-ttu-id="4a987-102">Non-SQL Server Subscribers</span><span class="sxs-lookup"><span data-stu-id="4a987-102">Non-SQL Server Subscribers</span></span>
  <span data-ttu-id="4a987-103">다음[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자는 밀어넣기 구독을 사용하여 스냅샷 및 트랜잭션 게시를 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-103">The following non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers can subscribe to snapshot and transactional publications using push subscriptions.</span></span> <span data-ttu-id="4a987-104">구독은 나열된 OLE DB 공급자의 최신 버전을 사용하는 나열된 각 데이터베이스의 가장 최신 버전 두 개에 대해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-104">Subscriptions are supported for the two most recent versions of each database listed using the most recent version of the OLE DB provider listed.</span></span>  
  
 <span data-ttu-id="4a987-105">SQL Server 이외의 구독자에 대한 다른 유형의 복제는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-105">Heterogeneous replication to non-SQL Server subscribers is deprecated.</span></span> <span data-ttu-id="4a987-106">Oracle 게시는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-106">Oracle Publishing is deprecated.</span></span> <span data-ttu-id="4a987-107">데이터를 이동하려면 변경 데이터 캡처 및 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]를 사용하여 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-107">To move data, create solutions using change data capture and [!INCLUDE[ssIS](../../../includes/ssis-md.md)].</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
|<span data-ttu-id="4a987-108">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="4a987-108">Database</span></span>|<span data-ttu-id="4a987-109">운영 체제</span><span class="sxs-lookup"><span data-stu-id="4a987-109">Operating System</span></span>|<span data-ttu-id="4a987-110">공급자</span><span class="sxs-lookup"><span data-stu-id="4a987-110">Provider</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="4a987-111">Oracle</span><span class="sxs-lookup"><span data-stu-id="4a987-111">Oracle</span></span>|<span data-ttu-id="4a987-112">Oracle에서 지원하는 모든 플랫폼</span><span class="sxs-lookup"><span data-stu-id="4a987-112">All platforms that Oracle supports</span></span>|<span data-ttu-id="4a987-113">Oracle OLE DB 공급자(Oracle에서 제공)</span><span class="sxs-lookup"><span data-stu-id="4a987-113">Oracle OLE DB provider (supplied by Oracle)</span></span>|  
|<span data-ttu-id="4a987-114">IBM DB2</span><span class="sxs-lookup"><span data-stu-id="4a987-114">IBM DB2</span></span>|<span data-ttu-id="4a987-115">MVS, AS400, Unix, Linux, Windows 9.x 이상(9.x 제외)</span><span class="sxs-lookup"><span data-stu-id="4a987-115">MVS, AS400, Unix, Linux, Windows excluding 9.x</span></span>|<span data-ttu-id="4a987-116">Microsoft HIS(Host Integration Server) OLE DB 공급자</span><span class="sxs-lookup"><span data-stu-id="4a987-116">Microsoft Host Integration Server (HIS) OLE DB provider</span></span>|  
  
 <span data-ttu-id="4a987-117">Oracle 및 IBM DB2,에 구독을 만드는 방법은 [Oracle 구독자](oracle-subscribers.md) 및 [IBM DB2 Subscribers](ibm-db2-subscribers.md)를 사용하여 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-117">For information about creating subscriptions to Oracle and IBM DB2, see [Oracle Subscribers](oracle-subscribers.md) and [IBM DB2 Subscribers](ibm-db2-subscribers.md).</span></span>  
  
## <a name="considerations-for-non-sql-server-subscribers"></a><span data-ttu-id="4a987-118">SQL Server 이외 구독자에 대한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="4a987-118">Considerations for Non-SQL Server Subscribers</span></span>  
 <span data-ttu-id="4a987-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자로 복제 시 다음 사항을 고려하십시오.</span><span class="sxs-lookup"><span data-stu-id="4a987-119">Keep the following considerations in mind when replicating to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
### <a name="general-considerations"></a><span data-ttu-id="4a987-120">일반적인 고려 사항</span><span class="sxs-lookup"><span data-stu-id="4a987-120">General Considerations</span></span>  
  
-   <span data-ttu-id="4a987-121">복제는 테이블 및 인덱싱된 뷰를[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자에 테이블로 게시하는 기능을 지원합니다. 인덱싱된 뷰는 인덱싱된 뷰로 복제될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-121">Replication supports publishing tables and indexed views as tables to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers (indexed views cannot be replicated as indexed views).</span></span>  
  
-   <span data-ttu-id="4a987-122">새 게시 마법사에서 게시를 만든 다음 게시 속성 대화 상자를 사용 하 여 SQL Server 이외 구독자에 대해 게시 속성 대화 상자를 사용 하 여 해당 게시를 사용 하도록 설정 하면 이외 구독자의 경우 구독 데이터베이스에 있는 모든 개체의 소유자가 지정 되지 않지만 구독자의 경우에는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 게시 데이터베이스의 해당 개체 소유자로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-122">When creating a publication in the New Publication Wizard and then enabling it for non-SQL Server Subscribers using the Publication Properties dialog box, the owner of all objects in the subscription database is not specified for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, whereas for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, it is set to the owner of the corresponding object in the publication database.</span></span>  
  
-   <span data-ttu-id="4a987-123">게시에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구독자와[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자가 있는 경우[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 구독자에 대한 구독을 만들기 전에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자에서 게시를 사용할 수 있도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-123">If a publication will have [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers and non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, the publication must be enabled for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers before any subscriptions to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers are created.</span></span>  
  
-   <span data-ttu-id="4a987-124">기본적으로[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자에 대해 스냅샷 에이전트에 의해 생성된 스크립트는 CREATE TABLE 구문에 따옴표가 붙지 않은 식별자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-124">By default, scripts generated by the Snapshot Agent for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers use non-quoted identifiers in the CREATE TABLE syntax.</span></span> <span data-ttu-id="4a987-125">따라서 이름이 'test'인 게시된 테이블이 'TEST'로 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-125">Therefore, a published table named 'test' is replicated as 'TEST'.</span></span> <span data-ttu-id="4a987-126">게시 데이터베이스에 있는 테이블에서와 똑같이 대/소문자를 맞추려면 배포 에이전트에 대해 **-QuotedIdentifier** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-126">To use the same case as the table in the publication database, use the **-QuotedIdentifier** parameter for the Distribution Agent.</span></span> <span data-ttu-id="4a987-127">게시된 개체 이름(테이블, 열 및 제약 조건)에 **이외 구독자의 데이터베이스 버전에서 예약된 단어나 공백이 포함되어 있으면** -QuotedIdentifier[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 매개 변수도 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-127">The **-QuotedIdentifier** parameter must also be used if published object names (such as tables, columns, and constraints) include spaces or words that are reserved words in the version of the database at the non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscriber.</span></span> <span data-ttu-id="4a987-128">이 매개 변수에 대한 자세한 내용은 [복제 배포 에이전트](../agents/replication-distribution-agent.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4a987-128">For more information about this parameter, see [Replication Distribution Agent](../agents/replication-distribution-agent.md).</span></span>  
  
-   <span data-ttu-id="4a987-129">배포 에이전트를 실행하는 계정에는 OLE DB 공급자의 설치 디렉터리에 대해 읽기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-129">The account under which the Distribution Agent runs must have read access to the install directory of the OLE DB provider.</span></span>  
  
-   <span data-ttu-id="4a987-130">기본적으로[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자의 경우 배포 에이전트는 구독 데이터베이스에 대해 [(기본 대상)] 값을 사용하고 배포 에이전트에 대해서는 **-SubscriberDB** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-130">By default for non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers, the Distribution Agent uses a value of [(default destination)] for the subscription database (the **-SubscriberDB** parameter for the Distribution Agent):</span></span>  
  
    -   <span data-ttu-id="4a987-131">Oracle의 경우 한 대의 서버에 데이터베이스가 하나만 있으므로 데이터베이스를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-131">For Oracle, a server has at most one database, so it is not necessary to specify the database.</span></span>  
  
    -   <span data-ttu-id="4a987-132">IBM DB2의 경우 데이터베이스는 DB2 연결 문자열에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-132">For IBM DB2, the database is specified in the DB2 connection string.</span></span> <span data-ttu-id="4a987-133">자세한 내용은 [SQL Server 이외 구독자에 대한 구독 만들기](../create-a-subscription-for-a-non-sql-server-subscriber.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a987-133">For more information, see [Create a Subscription for a Non-SQL Server Subscriber](../create-a-subscription-for-a-non-sql-server-subscriber.md).</span></span>  
  
-   <span data-ttu-id="4a987-134">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자가 64비트 플랫폼에서 실행되는 경우 적절한 64비트 버전의 OLE DB 공급자를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-134">If the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor is running on a 64 bit platform, you must use the 64 bit version of the appropriate OLE DB provider.</span></span>  
  
-   <span data-ttu-id="4a987-135">복제는 게시자와 구독자에 사용되는 데이터 정렬/코드 페이지에 관계없이 데이터를 유니코드 형식으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-135">Replication moves data in Unicode format regardless of the collation/code pages used on the Publisher and Subscriber.</span></span> <span data-ttu-id="4a987-136">게시자와 구독자 간에 복제할 때는 호환 가능한 데이터 정렬/코드 페이지를 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-136">It is recommended that you choose a compatible collation/code page when replicating between Publishers and Subscribers.</span></span>  
  
-   <span data-ttu-id="4a987-137">게시에서 아티클을 추가하거나 삭제하면[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자에 대한 구독을 다시 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-137">If an article is added to or deleted from a publication, subscriptions to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers must be reinitialized.</span></span>  
  
-   <span data-ttu-id="4a987-138">모든[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자에 대해 지원되는 유일한 제약 조건은 NULL 및 NOT NULL입니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-138">The only constraints supported for all non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers are: NULL, and NOT NULL.</span></span> <span data-ttu-id="4a987-139">PRIMARY KEY 제약 조건은 고유 인덱스로 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-139">Primary key constraints are replicated as unique indexes.</span></span>  
  
-   <span data-ttu-id="4a987-140">빈 값, 빈 문자열 및 NULL이 표시되는 방법에 영향을 주는 NULL 값은 다른 데이터베이스와 다르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-140">The value NULL is treated differently by different databases, which affects how a blank value, an empty string, and a NULL are represented.</span></span> <span data-ttu-id="4a987-141">이로 인해 UNIQUE 제약 조건이 정의된 열에 삽입된 값의 동작도 영향을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-141">This in turn affects the behavior of values inserted into columns with unique constraints defined.</span></span> <span data-ttu-id="4a987-142">예를 들어 Oracle에서는 고유하다고 판단되는 열에 여러 NULL 값을 사용할 수 있지만 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서는 고유 열에 NULL 값을 하나만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-142">For example, Oracle allows multiple NULL values in a column that is considered unique, whereas [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] allows only a single NULL value in a unique column.</span></span>  
  
     <span data-ttu-id="4a987-143">또 다른 요인으로는 열이 NOT NULL로 정의된 경우 NULL 값, 빈 문자열 및 빈 값이 처리되는 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-143">An additional factor is how NULL values, empty strings, and blank values are treated when the column is defined as NOT NULL.</span></span> <span data-ttu-id="4a987-144">Oracle 구독자에 대해 이러한 문제를 해결하는 방법은 [Oracle 구독자](oracle-subscribers.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4a987-144">For information about addressing this issue for Oracle Subscribers, see [Oracle Subscribers](oracle-subscribers.md).</span></span>  
  
-   <span data-ttu-id="4a987-145">복제 관련 메타데이터(트랜잭션 시퀀스 테이블)는 구독이 제거될 때[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자에서 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-145">Replication-related metadata (transaction sequence table) is not deleted from non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] subscribers when the subscription is removed.</span></span>  
  
### <a name="conforming-to-the-requirements-of-the-subscriber-database"></a><span data-ttu-id="4a987-146">구독자 데이터베이스의 요구 사항 준수</span><span class="sxs-lookup"><span data-stu-id="4a987-146">Conforming to the Requirements of the Subscriber Database</span></span>  
  
-   <span data-ttu-id="4a987-147">게시된 스키마와 데이터는 구독자에서 데이터베이스 요구 사항을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-147">Published schema and data must conform to the requirements of the database at the Subscriber.</span></span> <span data-ttu-id="4a987-148">예를 들어[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 데이터베이스의 최대 행 크기가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 최대 행 크기보다 작은 경우 게시된 스키마와 데이터가 이 크기를 초과하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-148">For example, if a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database has a smaller maximum row size than [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], you must ensure that the published schema and data do not exceed this size.</span></span>  
  
-   <span data-ttu-id="4a987-149">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자에 복제된 테이블은 구독자에서 데이터베이스의 테이블 명명 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-149">Tables replicated to non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers will adopt the table naming conventions of the database at the Subscriber.</span></span>  
  
-   <span data-ttu-id="4a987-150">SQL Server 이외 게시자에 대해서는 DDL이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-150">DDL is not supported for non-SQL Server Subscribers.</span></span> <span data-ttu-id="4a987-151">스키마 변경에 대한 자세한 내용은 [게시 데이터베이스의 스키마 변경](../publish/make-schema-changes-on-publication-databases.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a987-151">For more information about schema changes, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
### <a name="replication-feature-support"></a><span data-ttu-id="4a987-152">복제 기능 지원</span><span class="sxs-lookup"><span data-stu-id="4a987-152">Replication Feature Support</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="4a987-153">에서는 두 가지 유형의 구독(밀어넣기 및 끌어오기)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-153">offers two types of subscriptions: push and pull.</span></span> <span data-ttu-id="4a987-154">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자는 배포 에이전트가 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 배포자에서 실행되는 밀어넣기 구독을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-154">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers must use push subscriptions, in which the Distribution Agent runs at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="4a987-155">에서는 네이티브 bcp 모드 스냅샷과 문자 모드 스냅샷을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-155">offers two snapshot formats: native bcp-mode and character-mode.</span></span> <span data-ttu-id="4a987-156">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자에는 문자 모드 스냅샷이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-156">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers require character mode snapshots.</span></span>  
  
-   <span data-ttu-id="4a987-157">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자는 즉시 업데이트 구독 또는 지연 업데이트 구독을 사용할 수 없거나 피어 투 피어 토폴로지의 노드일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-157">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers cannot use immediate updating or queued updating subscriptions, or be nodes in a peer-to-peer topology.</span></span>  
  
-   <span data-ttu-id="4a987-158">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자는 백업을 사용하여 자동으로 초기화될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4a987-158">Non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers cannot be automatically initialized from a backup.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a987-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4a987-159">See Also</span></span>  
 <span data-ttu-id="4a987-160">[다른 유형의 데이터베이스 복제](heterogeneous-database-replication.md) </span><span class="sxs-lookup"><span data-stu-id="4a987-160">[Heterogeneous Database Replication](heterogeneous-database-replication.md) </span></span>  
 [<span data-ttu-id="4a987-161">게시 구독</span><span class="sxs-lookup"><span data-stu-id="4a987-161">Subscribe to Publications</span></span>](../subscribe-to-publications.md)  
  
  
