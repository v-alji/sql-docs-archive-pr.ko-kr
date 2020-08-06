---
title: 쿼리 옵션 실행 (고급 페이지) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.advanced.f1
ms.assetid: 661595ce-99b9-4316-ad80-ed04002d04d5
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: ''
ms.date: 09/03/2019
ms.openlocfilehash: 5b6ab8cc3c788e27946ddb68a3c926e8f926ebd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736741"
---
# <a name="query-options-execution-advanced-page"></a><span data-ttu-id="9d3fa-102">쿼리 옵션 실행(고급 페이지)</span><span class="sxs-lookup"><span data-stu-id="9d3fa-102">Query Options Execution (Advanced Page)</span></span>

  <span data-ttu-id="9d3fa-103">**SET** 문을 사용하여 다양한 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-103">A variety of options are available using the **SET** statement.</span></span> <span data-ttu-id="9d3fa-104">이 페이지를 사용 하 여 Microsoft SQL Server 쿼리를 실행 하는 **SET** 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-104">Use this page to specify a **SET** option to run Microsoft SQL Server queries.</span></span> <span data-ttu-id="9d3fa-105">이러한 각 옵션에 대한 자세한 내용은 SQL Server 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-105">For detailed information on each of these options, see SQL Server Books Online.</span></span>
  
<span data-ttu-id="9d3fa-106">**SET NOCOUNT** 는 결과 집합이 포함 된 메시지로 행의 수를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-106">**SET NOCOUNT** Doesn't return the count of the number of rows, as a message with the result set.</span></span> <span data-ttu-id="9d3fa-107">이 옵션은 기본적으로 선택 취소되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-107">This option is cleared by default.</span></span>

<span data-ttu-id="9d3fa-108">**NOEXEC 설정** 쿼리를 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-108">**SET NOEXEC** Doesn't run the query.</span></span> <span data-ttu-id="9d3fa-109">이 옵션은 기본적으로 선택 취소되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-109">This option is cleared by default.</span></span>

<span data-ttu-id="9d3fa-110">**PARSEONLY 설정** 각 쿼리의 구문을 검사 하지만 쿼리를 실행 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-110">**SET PARSEONLY** Checks the syntax of each query but Doesn't run the queries.</span></span> <span data-ttu-id="9d3fa-111">이 옵션은 기본적으로 선택 취소되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-111">This option is cleared by default.</span></span>  

<span data-ttu-id="9d3fa-112">**CONCAT_NULL_YIELDS_NULL 설정** 이 확인란을 선택 하면 기존 값을와 연결 하는 쿼리는 `NULL` 항상를 `NULL` 결과로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-112">**SET CONCAT_NULL_YIELDS_NULL** When this check box is selected, queries that concatenate an existing value with a `NULL`, always return a `NULL` as the result.</span></span> <span data-ttu-id="9d3fa-113">이 확인란의 선택을 취소하면 `NULL`에 연결된 기존 값이 기존 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-113">When this check box is cleared, an existing value concatenated with a `NULL`, returns the existing value.</span></span> <span data-ttu-id="9d3fa-114">이 옵션은 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-114">This option is selected by default.</span></span>

<span data-ttu-id="9d3fa-115">**ARITHABORT 설정** 이 확인란을 선택 하면 식을 평가 하는 `INSERT` `DELETE` 동안, 또는 `UPDATE` 문에 산술 오류 (오버플로, 0으로 나누기 또는 도메인 오류)가 발생할 때 쿼리 또는 일괄 처리가 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-115">**SET ARITHABORT** When this check box is selected, when an `INSERT`, `DELETE` or `UPDATE` statement encounters an arithmetic error (overflow, divide-by-zero, or a domain error) during expression evaluation the query or batch is terminated.</span></span> <span data-ttu-id="9d3fa-116">이 확인란의 선택을 취소하면 가능한 경우 해당 값으로 `NULL` 이 제공되고 쿼리가 계속된 다음 결과에 메시지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-116">When this check box is cleared, a `NULL` is provided for that value if possible, the query continues, and a message is included with the result.</span></span> <span data-ttu-id="9d3fa-117">이 동작에 대한 자세한 설명은 온라인 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-117">See Books Online for a more extensive description of this behavior.</span></span> <span data-ttu-id="9d3fa-118">이 옵션은 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-118">This option is selected by default.</span></span>
  
<span data-ttu-id="9d3fa-119">**SHOWPLAN_TEXT 설정** 이 확인란을 선택 하면 각 쿼리를 사용 하 여 쿼리 계획이 텍스트 형식으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-119">**SET SHOWPLAN_TEXT** When this check box is selected, the query plan is returned in text form with each query.</span></span> <span data-ttu-id="9d3fa-120">이 옵션은 기본적으로 선택 취소되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-120">This option is cleared by default.</span></span>
  
<span data-ttu-id="9d3fa-121">**SET STATISTICS TIME** 이 확인란을 선택하면 각 쿼리의 시간 통계가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-121">**SET STATISTICS TIME** When this check box is selected, the time statistics are returned with each query.</span></span> <span data-ttu-id="9d3fa-122">이 옵션은 기본적으로 선택 취소되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-122">This option is cleared by default.</span></span>
  
<span data-ttu-id="9d3fa-123">**통계 IO 설정** 이 확인란을 선택 하면 각 쿼리와 함께 i/o (입/출력) 관련 통계가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-123">**SET STATISTICS IO** When this check box is selected, statistics regarding input/output (I/O) are returned with each query.</span></span> <span data-ttu-id="9d3fa-124">이 옵션은 기본적으로 선택 취소되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-124">This option is cleared by default.</span></span>
  
<span data-ttu-id="9d3fa-125">**SET TRANSACTION ISOLATION LEVEL** 기본적으로 READ COMMITTED 트랜잭션 격리 수준이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-125">**SET TRANSACTION ISOLATION LEVEL** The READ COMMITTED transaction isolation level is set by default.</span></span> <span data-ttu-id="9d3fa-126">자세한 내용은 [SET TRANSACTION ISOLATION LEVEL&#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-126">For more information, see [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span> <span data-ttu-id="9d3fa-127">SNAPSHOT 트랜잭션 격리 수준을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-127">SNAPSHOT transaction isolation level isn't available.</span></span> <span data-ttu-id="9d3fa-128">SNAPSHOT 격리를 사용하려면 다음 [!INCLUDE[tsql](../includes/tsql-md.md)] 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-128">To use SNAPSHOT isolation, add the following [!INCLUDE[tsql](../includes/tsql-md.md)] statement:</span></span>
  
  ```sql
  SET TRANSACTION ISOLATION LEVEL SNAPSHOT;
  GO
  ```

<span data-ttu-id="9d3fa-129">**SET DEADLOCK PRIORITY** 기본값 **Normal** 로 설정하면 교착 상태가 발생할 때 각 쿼리의 우선 순위가 같아집니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-129">**SET DEADLOCK PRIORITY** The default value of **Normal** allows each query to have the same priority when a deadlock occurs.</span></span> <span data-ttu-id="9d3fa-130">이 쿼리를 교착 상태를 해제하고 종료할 쿼리로 선택하려면 드롭다운 목록에서 Low 우선 순위를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-130">Select the priority Low from the drop-down list, if you want this query to lose any deadlock conflict and be selected as the query to be terminated.</span></span>

<span data-ttu-id="9d3fa-131">**잠금 제한 시간 설정** 기본값-1은 트랜잭션이 완료 될 때까지 잠금이 유지 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-131">**SET LOCK TIMEOUT** The default value of -1 indicates that locks are held until transactions are completed.</span></span> <span data-ttu-id="9d3fa-132">0은 기다리지 않음을 나타내고 잠금이 있으면 바로 오류 메시지가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-132">A value of 0 means not to wait at all and return a message as soon as a lock is encountered.</span></span> <span data-ttu-id="9d3fa-133">트랜잭션 잠금을 이 시간보다 오래 유지해야 하는 경우 0밀리초보다 큰 값을 지정하여 트랜잭션을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-133">Provide a value of greater than 0 milliseconds to terminate a transaction if the locks for transaction must be held for greater than that time.</span></span>

<span data-ttu-id="9d3fa-134">**QUERY_GOVERNOR_COST_LIMIT 설정** Query **governor cost limit** 옵션을 사용 하 여 쿼리가 실행 될 수 있는 기간의 상한을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-134">**SET QUERY_GOVERNOR_COST_LIMIT** Use the **query governor cost limit** option to specify an upper limit on the time period in which a query can run.</span></span> <span data-ttu-id="9d3fa-135">쿼리 비용이란 특정 하드웨어 구성에서 쿼리를 완료하는 데 필요한 예상 소요 시간(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-135">Query cost refers to the estimated elapsed time, in seconds, required to complete a query on a specific hardware configuration.</span></span> <span data-ttu-id="9d3fa-136">기본값 0은 쿼리 실행 제한 시간이 없다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-136">The default setting of 0 indicates no limit to the length of time a query will run</span></span>

<span data-ttu-id="9d3fa-137">**공급자 메시지 헤더 표시 안 함** 이 확인란을 선택 하면 공급자의 상태 메시지 (예: OLE DB 공급자)가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-137">**Suppress provider message headers** When this check box is selected, status messages from the provider (such as the OLE DB provider) aren't displayed.</span></span> <span data-ttu-id="9d3fa-138">이 확인란은 기본적으로 선택되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-138">This check box is selected by default.</span></span> <span data-ttu-id="9d3fa-139">공급자 수준에서 오류가 발생할 수 있는 쿼리 문제를 해결할 때 공급자 메시지를 보려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-139">Clear this check box to see the provider messages when troubleshooting queries that may be failing at the provider level.</span></span>

<span data-ttu-id="9d3fa-140">**쿼리 실행 후 연결 끊기** 이 확인란을 선택하면 쿼리 완료 후 SQL Server에 대한 연결이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-140">**Disconnect after the query executes** When this check box is selected, the connection to SQL Server is terminated after the query completes.</span></span> <span data-ttu-id="9d3fa-141">이 옵션은 기본적으로 선택 취소되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-141">This option is cleared by default.</span></span>

<span data-ttu-id="9d3fa-142">**완료 시간 표시** 쿼리 결과 또는 메시지 탭 후에 쿼리 실행이 완료 된 시간을 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-142">**Show completion time** Allows you to print the time at which the query execution completed either after the query results or in the messages tab.</span></span>

<span data-ttu-id="9d3fa-143">**Always Encrypted에 대 한 VBS enclaves 용 증명 프로토콜** Secure enclaves로 상시 암호화에 사용 되는 VBS (가상화 기반 보안) enclaves 증명 프로토콜을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-143">**Attestation protocol for VBS enclaves for Always Encrypted** Allows you to set an attestation protocol for Virtualization Based Security (VBS) enclaves used by always Encrypted with secure enclaves.</span></span>

<span data-ttu-id="9d3fa-144">현재 지원 되는 증명 프로토콜은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-144">The current supported attestation protocols are:</span></span>

* <span data-ttu-id="9d3fa-145">호스트 보호 서비스-Windows HGS (호스트 보호 서비스)를 사용 하는 증명 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-145">Host Guardian Service - an attestation protocol using Windows Host Guardian Service (HGS).</span></span>

<span data-ttu-id="9d3fa-146">자세한 내용은 [secure enclaves](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions) 및 [secure Enclave 증명](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation)을 사용 하는 Always Encrypted를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-146">For more information, see [Always Encrypted with secure enclaves](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions) and [Secure Enclave Attestation](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-enclaves?view=sqlallproducts-allversions#secure-enclave-attestation).</span></span>

<span data-ttu-id="9d3fa-147">**기본값으로 다시 설정** 이 페이지의 모든 값을 원래 기본값으로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9d3fa-147">**Reset to Default** Resets all values on this page to the original default values.</span></span>
