---
title: Oracle 게시자에 대한 관리 고려 사항 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], administrative considerations
- administering replication, Oracle publishing
ms.assetid: cfd81fb5-419b-4a1b-97c4-be7c9d4ee289
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3104b507987a4a236d39dd0ae1f8e3c29358c730
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653276"
---
# <a name="administrative-considerations-for-oracle-publishers"></a><span data-ttu-id="b212d-102">Oracle 게시자에 대한 관리 고려 사항</span><span class="sxs-lookup"><span data-stu-id="b212d-102">Administrative Considerations for Oracle Publishers</span></span>
  <span data-ttu-id="b212d-103">Oracle 게시자를 구성하고 복제 변경 내용 추적 메커니즘을 설정한 후에도 Oracle 데이터베이스 시스템의 관리자는 표준 Oracle 데이터베이스 유틸리티를 사용하고 일반 시스템 관리 태스크를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-103">After an Oracle Publisher is configured and the replication change tracking mechanisms are in place, administrators of the Oracle database system can still use standard Oracle database utilities and perform typical system administration tasks.</span></span> <span data-ttu-id="b212d-104">그러나 특정 관리 태스크 수행 시 게시된 데이터에 미치는 영향을 알아두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-104">However, you should be aware of the effects on the published data of performing certain administrative tasks.</span></span>  
  
 <span data-ttu-id="b212d-105">복제에 대해 게시된 열을 삭제 또는 수정하거나 복제 개체를 삭제 또는 수정하는 경우를 제외하고 다음 고려 사항은 스냅샷 게시에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-105">With the exception of dropping or modifying a column that is published for replication, or dropping or modifying any replication objects, these considerations do not apply to snapshot publications.</span></span>  
  
## <a name="importing-and-loading-data"></a><span data-ttu-id="b212d-106">데이터 가져오기 및 로드</span><span class="sxs-lookup"><span data-stu-id="b212d-106">Importing and loading data</span></span>  
 <span data-ttu-id="b212d-107">트리거는 Oracle의 트랜잭션 게시에 대한 변경 내용 추적에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-107">Triggers are used in change tracking for transactional publications on Oracle.</span></span> <span data-ttu-id="b212d-108">게시된 테이블에 대한 변경 내용은 업데이트, 삽입 또는 삭제가 발생할 때 복제 트리거가 실행되는 경우에만 구독자로 복제될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-108">Changes to published tables can be replicated to Subscribers only if the replication triggers fire when an update, insert, or delete occurs.</span></span> <span data-ttu-id="b212d-109">Oracle 유틸리티인 Oracle Import 및 SQL\*Loader에는 모두 이러한 유틸리티를 사용하여 복제된 테이블에 행을 삽입할 때 트리거의 발생 여부에 영향을 주는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-109">The Oracle utilities Oracle Import and SQL\*Loader both have options that affect whether triggers will fire when rows are inserted into replicated tables with these utilities.</span></span>  
  
### <a name="oracle-import"></a><span data-ttu-id="b212d-110">Oracle Import</span><span class="sxs-lookup"><span data-stu-id="b212d-110">Oracle Import</span></span>  
 <span data-ttu-id="b212d-111">Oracle Import에서는 **ignore** 옵션을 'y' 또는 'n'으로 설정할 수 있습니다(기본값: 'n').</span><span class="sxs-lookup"><span data-stu-id="b212d-111">With Oracle Import, you can set the option **ignore** to 'y' or 'n' (the default is 'n').</span></span> <span data-ttu-id="b212d-112">**ignore** 를 'n'으로 설정하면 가져오기 작업을 수행하는 동안 테이블이 삭제되고 다시 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-112">If **ignore** is set to 'n', the table is dropped and re-created during import.</span></span> <span data-ttu-id="b212d-113">이렇게 하면 복제 트리거가 제거되고 복제는 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-113">This removes replication triggers and disables replication.</span></span> <span data-ttu-id="b212d-114">**ignore** 를 'y'로 설정하면 가져오기 작업에서 행을 기존 테이블로 로드하려고 하며 이로 인해 복제 트리거가 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-114">If **ignore** is set to 'y', import will attempt to load the rows into the existing table, which fires the replication triggers.</span></span> <span data-ttu-id="b212d-115">그러므로 가져오기 도구를 사용하여 복제된 테이블로 가져올 때는 **ignore** 를 'y'로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-115">Therefore, ensure **ignore** is set to 'y' when importing into a replicated table with the Import tool.</span></span>  
  
### <a name="sqlloader"></a><span data-ttu-id="b212d-116">SQL\*Loader</span><span class="sxs-lookup"><span data-stu-id="b212d-116">SQL\*Loader</span></span>  
 <span data-ttu-id="b212d-117">SQL\*Loader에서는 **direct** 옵션을 'true' 또는 'false'로 설정할 수 있습니다(기본값: 'false').</span><span class="sxs-lookup"><span data-stu-id="b212d-117">With SQL\*Loader, you can set the option **direct** to 'true' or 'false' (the default is 'false').</span></span> <span data-ttu-id="b212d-118">**direct** 를 'false'로 설정하면 기존 INSERT 문을 사용하여 행이 삽입되고 이로 인해 복제 트리거가 발생됩니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-118">If **direct** is set to 'false', rows are inserted using conventional INSERT statements, which fire replication triggers.</span></span> <span data-ttu-id="b212d-119">**direct** 를 'true'로 설정하면 로드는 최적화되지만 트리거가 발생되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-119">If **direct** is set to 'true', the load is optimized, and triggers are not fired.</span></span> <span data-ttu-id="b212d-120">그러므로 SQL\*Loader 도구를 사용하여 복제된 테이블로 로드할 때는 **direct** 를 'false'로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-120">Therefore, ensure **direct** is set to 'false' when loading into a replicated table with the SQL\*Loader tool.</span></span>  
  
## <a name="making-changes-to-published-objects"></a><span data-ttu-id="b212d-121">게시된 개체 변경</span><span class="sxs-lookup"><span data-stu-id="b212d-121">Making changes to published objects</span></span>  
 <span data-ttu-id="b212d-122">다음 동작을 수행할 때 특별히 고려할 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-122">The following actions require no special considerations:</span></span>  
  
-   <span data-ttu-id="b212d-123">게시된 테이블에 인덱스 다시 작성</span><span class="sxs-lookup"><span data-stu-id="b212d-123">Rebuilding indexes on published tables.</span></span>  
  
-   <span data-ttu-id="b212d-124">게시된 테이블에 사용자 트리거 추가</span><span class="sxs-lookup"><span data-stu-id="b212d-124">Adding user triggers to a published table.</span></span>  
  
 <span data-ttu-id="b212d-125">다음 동작을 수행하려면 게시된 테이블에서의 모든 활동을 중지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-125">The following action requires you to stop all activity on the published tables:</span></span>  
  
-   <span data-ttu-id="b212d-126">게시된 테이블 이동</span><span class="sxs-lookup"><span data-stu-id="b212d-126">Moving a published table.</span></span>  
  
 <span data-ttu-id="b212d-127">다음 동작을 수행하려면 게시를 삭제하고 작업을 수행한 다음 게시를 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-127">The following actions require you to drop the publication, perform the operation, and then recreate the publication:</span></span>  
  
-   <span data-ttu-id="b212d-128">게시된 테이블 잘라내기</span><span class="sxs-lookup"><span data-stu-id="b212d-128">Truncating a published table.</span></span>  
  
-   <span data-ttu-id="b212d-129">게시된 테이블의 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="b212d-129">Renaming a published table.</span></span>  
  
-   <span data-ttu-id="b212d-130">게시된 테이블에 열 추가</span><span class="sxs-lookup"><span data-stu-id="b212d-130">Adding a column to a published table.</span></span>  
  
-   <span data-ttu-id="b212d-131">복제에 대해 게시된 열 삭제 또는 수정</span><span class="sxs-lookup"><span data-stu-id="b212d-131">Dropping or modifying a column that is published for replication.</span></span>  
  
-   <span data-ttu-id="b212d-132">로그되지 않는 작업 수행</span><span class="sxs-lookup"><span data-stu-id="b212d-132">Performing non-logged operations.</span></span>  
  
## <a name="dropping-or-modifying-replication-objects"></a><span data-ttu-id="b212d-133">복제 개체 삭제 또는 수정</span><span class="sxs-lookup"><span data-stu-id="b212d-133">Dropping or modifying replication objects</span></span>  
 <span data-ttu-id="b212d-134">게시자 수준의 추적 테이블, 트리거, 시퀀스 또는 저장 프로시저를 삭제하거나 수정할 경우 게시자를 삭제하고 다시 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b212d-134">You must drop and reconfigure the Publisher if you drop or modify any Publisher level tracking tables, triggers, sequences, or stored procedures.</span></span> <span data-ttu-id="b212d-135">이러한 개체의 일부 목록을 보려면 [Oracle 게시자에 생성되는 개체](objects-created-on-the-oracle-publisher.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b212d-135">For a partial list of these objects, see [Objects Created on the Oracle Publisher](objects-created-on-the-oracle-publisher.md).</span></span>  
  
 <span data-ttu-id="b212d-136">게시자를 삭제 및 다시 구성하는 방법은 [Troubleshooting Oracle Publishers](troubleshooting-oracle-publishers.md)항목의 "게시자를 다시 구성해야 하는 변경 내용이 적용되었습니다" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="b212d-136">For information about dropping and reconfiguring the Publisher, see the section "Changes are made that require reconfiguration of the Publisher" in the topic [Troubleshooting Oracle Publishers](troubleshooting-oracle-publishers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b212d-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b212d-137">See Also</span></span>  
 <span data-ttu-id="b212d-138">[Oracle 게시자 구성](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="b212d-138">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 <span data-ttu-id="b212d-139">[Oracle 게시자에 대한 디자인 고려 사항 및 제한 사항](design-considerations-and-limitations-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="b212d-139">[Design Considerations and Limitations for Oracle Publishers](design-considerations-and-limitations-for-oracle-publishers.md) </span></span>  
 [<span data-ttu-id="b212d-140">Oracle 게시 개요</span><span class="sxs-lookup"><span data-stu-id="b212d-140">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
