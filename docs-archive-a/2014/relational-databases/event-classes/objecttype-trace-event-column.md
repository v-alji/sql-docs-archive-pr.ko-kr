---
title: ObjectType 추적 이벤트 열 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Object Type column values
- events [SQL Server], Object Type column values
- event classes [SQL Server], Object Type column values
- Object Type column values [SQL Server]
ms.assetid: 42f85c50-34c9-49ca-955f-af9595e2707f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f90661e5ebedc91505989c3d80dcec78436ce86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648402"
---
# <a name="objecttype-trace-event-column"></a><span data-ttu-id="ca3ce-102">ObjectType 추적 이벤트 열</span><span class="sxs-lookup"><span data-stu-id="ca3ce-102">ObjectType Trace Event Column</span></span>
  <span data-ttu-id="ca3ce-103">Object Type 추적 이벤트 열은 다양한 추적 이벤트에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca3ce-103">The Object Type trace event column is used in a variety of trace events.</span></span> <span data-ttu-id="ca3ce-104">이 항목에서는 이 열에 사용할 수 있는 값과 해당 값의 정의에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ca3ce-104">This topic describes the possible values of this column and their associated definitions.</span></span>  
  
## <a name="object-type-column-values"></a><span data-ttu-id="ca3ce-105">Object Type 열 값</span><span class="sxs-lookup"><span data-stu-id="ca3ce-105">Object Type Column Values</span></span>  
  
|<span data-ttu-id="ca3ce-106">값</span><span class="sxs-lookup"><span data-stu-id="ca3ce-106">Value</span></span>|<span data-ttu-id="ca3ce-107">정의</span><span class="sxs-lookup"><span data-stu-id="ca3ce-107">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="ca3ce-108">8259</span><span class="sxs-lookup"><span data-stu-id="ca3ce-108">8259</span></span>|<span data-ttu-id="ca3ce-109">CHECK 제약 조건</span><span class="sxs-lookup"><span data-stu-id="ca3ce-109">Check Constraint</span></span>|  
|<span data-ttu-id="ca3ce-110">8260</span><span class="sxs-lookup"><span data-stu-id="ca3ce-110">8260</span></span>|<span data-ttu-id="ca3ce-111">기본값(제약 조건 또는 독립 실행)</span><span class="sxs-lookup"><span data-stu-id="ca3ce-111">Default (constraint or standalone)</span></span>|  
|<span data-ttu-id="ca3ce-112">8262</span><span class="sxs-lookup"><span data-stu-id="ca3ce-112">8262</span></span>|<span data-ttu-id="ca3ce-113">FOREIGN KEY 제약 조건</span><span class="sxs-lookup"><span data-stu-id="ca3ce-113">Foreign-key Constraint</span></span>|  
|<span data-ttu-id="ca3ce-114">8272</span><span class="sxs-lookup"><span data-stu-id="ca3ce-114">8272</span></span>|<span data-ttu-id="ca3ce-115">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="ca3ce-115">Stored Procedure</span></span>|  
|<span data-ttu-id="ca3ce-116">8274</span><span class="sxs-lookup"><span data-stu-id="ca3ce-116">8274</span></span>|<span data-ttu-id="ca3ce-117">규칙</span><span class="sxs-lookup"><span data-stu-id="ca3ce-117">Rule</span></span>|  
|<span data-ttu-id="ca3ce-118">8275</span><span class="sxs-lookup"><span data-stu-id="ca3ce-118">8275</span></span>|<span data-ttu-id="ca3ce-119">시스템 테이블</span><span class="sxs-lookup"><span data-stu-id="ca3ce-119">System Table</span></span>|  
|<span data-ttu-id="ca3ce-120">8276</span><span class="sxs-lookup"><span data-stu-id="ca3ce-120">8276</span></span>|<span data-ttu-id="ca3ce-121">서버에 대한 트리거</span><span class="sxs-lookup"><span data-stu-id="ca3ce-121">Trigger on Server</span></span>|  
|<span data-ttu-id="ca3ce-122">8277</span><span class="sxs-lookup"><span data-stu-id="ca3ce-122">8277</span></span>|<span data-ttu-id="ca3ce-123">사용자 정의 테이블</span><span class="sxs-lookup"><span data-stu-id="ca3ce-123">(User-defined) Table</span></span>|  
|<span data-ttu-id="ca3ce-124">8278</span><span class="sxs-lookup"><span data-stu-id="ca3ce-124">8278</span></span>|<span data-ttu-id="ca3ce-125">보기</span><span class="sxs-lookup"><span data-stu-id="ca3ce-125">View</span></span>|  
|<span data-ttu-id="ca3ce-126">8280</span><span class="sxs-lookup"><span data-stu-id="ca3ce-126">8280</span></span>|<span data-ttu-id="ca3ce-127">확장 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="ca3ce-127">Extended Stored Procedure</span></span>|  
|<span data-ttu-id="ca3ce-128">16724</span><span class="sxs-lookup"><span data-stu-id="ca3ce-128">16724</span></span>|<span data-ttu-id="ca3ce-129">CLR 트리거</span><span class="sxs-lookup"><span data-stu-id="ca3ce-129">CLR Trigger</span></span>|  
|<span data-ttu-id="ca3ce-130">16964</span><span class="sxs-lookup"><span data-stu-id="ca3ce-130">16964</span></span>|<span data-ttu-id="ca3ce-131">데이터베이스</span><span class="sxs-lookup"><span data-stu-id="ca3ce-131">Database</span></span>|  
|<span data-ttu-id="ca3ce-132">16975</span><span class="sxs-lookup"><span data-stu-id="ca3ce-132">16975</span></span>|<span data-ttu-id="ca3ce-133">Object</span><span class="sxs-lookup"><span data-stu-id="ca3ce-133">Object</span></span>|  
|<span data-ttu-id="ca3ce-134">17222</span><span class="sxs-lookup"><span data-stu-id="ca3ce-134">17222</span></span>|<span data-ttu-id="ca3ce-135">FullText 카탈로그</span><span class="sxs-lookup"><span data-stu-id="ca3ce-135">FullText Catalog</span></span>|  
|<span data-ttu-id="ca3ce-136">17232</span><span class="sxs-lookup"><span data-stu-id="ca3ce-136">17232</span></span>|<span data-ttu-id="ca3ce-137">CLR 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="ca3ce-137">CLR Stored Procedure</span></span>|  
|<span data-ttu-id="ca3ce-138">17235</span><span class="sxs-lookup"><span data-stu-id="ca3ce-138">17235</span></span>|<span data-ttu-id="ca3ce-139">스키마</span><span class="sxs-lookup"><span data-stu-id="ca3ce-139">Schema</span></span>|  
|<span data-ttu-id="ca3ce-140">17475</span><span class="sxs-lookup"><span data-stu-id="ca3ce-140">17475</span></span>|<span data-ttu-id="ca3ce-141">자격 증명</span><span class="sxs-lookup"><span data-stu-id="ca3ce-141">Credential</span></span>|  
|<span data-ttu-id="ca3ce-142">17491</span><span class="sxs-lookup"><span data-stu-id="ca3ce-142">17491</span></span>|<span data-ttu-id="ca3ce-143">DDL 이벤트</span><span class="sxs-lookup"><span data-stu-id="ca3ce-143">DDL Event</span></span>|  
|<span data-ttu-id="ca3ce-144">17741</span><span class="sxs-lookup"><span data-stu-id="ca3ce-144">17741</span></span>|<span data-ttu-id="ca3ce-145">관리 이벤트</span><span class="sxs-lookup"><span data-stu-id="ca3ce-145">Management Event</span></span>|  
|<span data-ttu-id="ca3ce-146">17747</span><span class="sxs-lookup"><span data-stu-id="ca3ce-146">17747</span></span>|<span data-ttu-id="ca3ce-147">보안 이벤트</span><span class="sxs-lookup"><span data-stu-id="ca3ce-147">Security Event</span></span>|  
|<span data-ttu-id="ca3ce-148">17749</span><span class="sxs-lookup"><span data-stu-id="ca3ce-148">17749</span></span>|<span data-ttu-id="ca3ce-149">사용자 이벤트</span><span class="sxs-lookup"><span data-stu-id="ca3ce-149">User Event</span></span>|  
|<span data-ttu-id="ca3ce-150">17985</span><span class="sxs-lookup"><span data-stu-id="ca3ce-150">17985</span></span>|<span data-ttu-id="ca3ce-151">CLR 집계 함수</span><span class="sxs-lookup"><span data-stu-id="ca3ce-151">CLR Aggregate Function</span></span>|  
|<span data-ttu-id="ca3ce-152">17993</span><span class="sxs-lookup"><span data-stu-id="ca3ce-152">17993</span></span>|<span data-ttu-id="ca3ce-153">인라인 테이블 반환 SQL 함수</span><span class="sxs-lookup"><span data-stu-id="ca3ce-153">Inline Table-valued SQL Function</span></span>|  
|<span data-ttu-id="ca3ce-154">18000</span><span class="sxs-lookup"><span data-stu-id="ca3ce-154">18000</span></span>|<span data-ttu-id="ca3ce-155">파티션 함수</span><span class="sxs-lookup"><span data-stu-id="ca3ce-155">Partition Function</span></span>|  
|<span data-ttu-id="ca3ce-156">18002</span><span class="sxs-lookup"><span data-stu-id="ca3ce-156">18002</span></span>|<span data-ttu-id="ca3ce-157">복제 필터 프로시저</span><span class="sxs-lookup"><span data-stu-id="ca3ce-157">Replication Filter Procedure</span></span>|  
|<span data-ttu-id="ca3ce-158">18004</span><span class="sxs-lookup"><span data-stu-id="ca3ce-158">18004</span></span>|<span data-ttu-id="ca3ce-159">테이블 반환 SQL 함수</span><span class="sxs-lookup"><span data-stu-id="ca3ce-159">Table-valued SQL Function</span></span>|  
|<span data-ttu-id="ca3ce-160">18259</span><span class="sxs-lookup"><span data-stu-id="ca3ce-160">18259</span></span>|<span data-ttu-id="ca3ce-161">서버 역할</span><span class="sxs-lookup"><span data-stu-id="ca3ce-161">Server Role</span></span>|  
|<span data-ttu-id="ca3ce-162">18263</span><span class="sxs-lookup"><span data-stu-id="ca3ce-162">18263</span></span>|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="ca3ce-163">Windows 그룹</span><span class="sxs-lookup"><span data-stu-id="ca3ce-163">Windows Group</span></span>|  
|<span data-ttu-id="ca3ce-164">19265</span><span class="sxs-lookup"><span data-stu-id="ca3ce-164">19265</span></span>|<span data-ttu-id="ca3ce-165">비대칭 키</span><span class="sxs-lookup"><span data-stu-id="ca3ce-165">Asymmetric Key</span></span>|  
|<span data-ttu-id="ca3ce-166">19277</span><span class="sxs-lookup"><span data-stu-id="ca3ce-166">19277</span></span>|<span data-ttu-id="ca3ce-167">마스터 키</span><span class="sxs-lookup"><span data-stu-id="ca3ce-167">Master Key</span></span>|  
|<span data-ttu-id="ca3ce-168">19280</span><span class="sxs-lookup"><span data-stu-id="ca3ce-168">19280</span></span>|<span data-ttu-id="ca3ce-169">기본 키</span><span class="sxs-lookup"><span data-stu-id="ca3ce-169">Primary Key</span></span>|  
|<span data-ttu-id="ca3ce-170">19283</span><span class="sxs-lookup"><span data-stu-id="ca3ce-170">19283</span></span>|<span data-ttu-id="ca3ce-171">ObfusKey</span><span class="sxs-lookup"><span data-stu-id="ca3ce-171">ObfusKey</span></span>|  
|<span data-ttu-id="ca3ce-172">19521</span><span class="sxs-lookup"><span data-stu-id="ca3ce-172">19521</span></span>|<span data-ttu-id="ca3ce-173">비대칭 키 로그인</span><span class="sxs-lookup"><span data-stu-id="ca3ce-173">Asymmetric Key Login</span></span>|  
|<span data-ttu-id="ca3ce-174">19523</span><span class="sxs-lookup"><span data-stu-id="ca3ce-174">19523</span></span>|<span data-ttu-id="ca3ce-175">인증서 로그인</span><span class="sxs-lookup"><span data-stu-id="ca3ce-175">Certificate Login</span></span>|  
|<span data-ttu-id="ca3ce-176">19538</span><span class="sxs-lookup"><span data-stu-id="ca3ce-176">19538</span></span>|<span data-ttu-id="ca3ce-177">역할</span><span class="sxs-lookup"><span data-stu-id="ca3ce-177">Role</span></span>|  
|<span data-ttu-id="ca3ce-178">19539</span><span class="sxs-lookup"><span data-stu-id="ca3ce-178">19539</span></span>|<span data-ttu-id="ca3ce-179">SQL 로그인</span><span class="sxs-lookup"><span data-stu-id="ca3ce-179">SQL Login</span></span>|  
|<span data-ttu-id="ca3ce-180">19543</span><span class="sxs-lookup"><span data-stu-id="ca3ce-180">19543</span></span>|<span data-ttu-id="ca3ce-181">Windows 로그인</span><span class="sxs-lookup"><span data-stu-id="ca3ce-181">Windows Login</span></span>|  
|<span data-ttu-id="ca3ce-182">20034</span><span class="sxs-lookup"><span data-stu-id="ca3ce-182">20034</span></span>|<span data-ttu-id="ca3ce-183">원격 서비스 바인딩</span><span class="sxs-lookup"><span data-stu-id="ca3ce-183">Remote Service Binding</span></span>|  
|<span data-ttu-id="ca3ce-184">20036</span><span class="sxs-lookup"><span data-stu-id="ca3ce-184">20036</span></span>|<span data-ttu-id="ca3ce-185">데이터베이스에 대한 이벤트 알림</span><span class="sxs-lookup"><span data-stu-id="ca3ce-185">Event Notification on Database</span></span>|  
|<span data-ttu-id="ca3ce-186">20037</span><span class="sxs-lookup"><span data-stu-id="ca3ce-186">20037</span></span>|<span data-ttu-id="ca3ce-187">이벤트 알림</span><span class="sxs-lookup"><span data-stu-id="ca3ce-187">Event Notification</span></span>|  
|<span data-ttu-id="ca3ce-188">20038</span><span class="sxs-lookup"><span data-stu-id="ca3ce-188">20038</span></span>|<span data-ttu-id="ca3ce-189">스칼라 SQL 함수</span><span class="sxs-lookup"><span data-stu-id="ca3ce-189">Scalar SQL Function</span></span>|  
|<span data-ttu-id="ca3ce-190">20047</span><span class="sxs-lookup"><span data-stu-id="ca3ce-190">20047</span></span>|<span data-ttu-id="ca3ce-191">개체에 대한 이벤트 알림</span><span class="sxs-lookup"><span data-stu-id="ca3ce-191">Event Notification on Object</span></span>|  
|<span data-ttu-id="ca3ce-192">20051</span><span class="sxs-lookup"><span data-stu-id="ca3ce-192">20051</span></span>|<span data-ttu-id="ca3ce-193">동의어</span><span class="sxs-lookup"><span data-stu-id="ca3ce-193">Synonym</span></span>|  
|<span data-ttu-id="ca3ce-194">20307</span><span class="sxs-lookup"><span data-stu-id="ca3ce-194">20307</span></span>|<span data-ttu-id="ca3ce-195">시퀀스</span><span class="sxs-lookup"><span data-stu-id="ca3ce-195">Sequence</span></span>|  
|<span data-ttu-id="ca3ce-196">20549</span><span class="sxs-lookup"><span data-stu-id="ca3ce-196">20549</span></span>|<span data-ttu-id="ca3ce-197">끝점</span><span class="sxs-lookup"><span data-stu-id="ca3ce-197">End Point</span></span>|  
|<span data-ttu-id="ca3ce-198">20801</span><span class="sxs-lookup"><span data-stu-id="ca3ce-198">20801</span></span>|<span data-ttu-id="ca3ce-199">캐시될 임시 쿼리</span><span class="sxs-lookup"><span data-stu-id="ca3ce-199">Adhoc Queries which may be cached</span></span>|  
|<span data-ttu-id="ca3ce-200">20816</span><span class="sxs-lookup"><span data-stu-id="ca3ce-200">20816</span></span>|<span data-ttu-id="ca3ce-201">캐시될 준비된 쿼리</span><span class="sxs-lookup"><span data-stu-id="ca3ce-201">Prepared Queries which may be cached</span></span>|  
|<span data-ttu-id="ca3ce-202">20819</span><span class="sxs-lookup"><span data-stu-id="ca3ce-202">20819</span></span>|<span data-ttu-id="ca3ce-203">Service Broker 서비스 큐</span><span class="sxs-lookup"><span data-stu-id="ca3ce-203">Service Broker Service Queue</span></span>|  
|<span data-ttu-id="ca3ce-204">20821</span><span class="sxs-lookup"><span data-stu-id="ca3ce-204">20821</span></span>|<span data-ttu-id="ca3ce-205">UNIQUE 제약 조건</span><span class="sxs-lookup"><span data-stu-id="ca3ce-205">Unique Constraint</span></span>|  
|<span data-ttu-id="ca3ce-206">21057</span><span class="sxs-lookup"><span data-stu-id="ca3ce-206">21057</span></span>|<span data-ttu-id="ca3ce-207">애플리케이션 역할</span><span class="sxs-lookup"><span data-stu-id="ca3ce-207">Application Role</span></span>|  
|<span data-ttu-id="ca3ce-208">21059</span><span class="sxs-lookup"><span data-stu-id="ca3ce-208">21059</span></span>|<span data-ttu-id="ca3ce-209">인증서</span><span class="sxs-lookup"><span data-stu-id="ca3ce-209">Certificate</span></span>|  
|<span data-ttu-id="ca3ce-210">21075</span><span class="sxs-lookup"><span data-stu-id="ca3ce-210">21075</span></span>|<span data-ttu-id="ca3ce-211">서버</span><span class="sxs-lookup"><span data-stu-id="ca3ce-211">Server</span></span>|  
|<span data-ttu-id="ca3ce-212">21076</span><span class="sxs-lookup"><span data-stu-id="ca3ce-212">21076</span></span>|<span data-ttu-id="ca3ce-213">Transact-SQL 트리거</span><span class="sxs-lookup"><span data-stu-id="ca3ce-213">Transact-SQL Trigger</span></span>|  
|<span data-ttu-id="ca3ce-214">21313</span><span class="sxs-lookup"><span data-stu-id="ca3ce-214">21313</span></span>|<span data-ttu-id="ca3ce-215">어셈블리</span><span class="sxs-lookup"><span data-stu-id="ca3ce-215">Assembly</span></span>|  
|<span data-ttu-id="ca3ce-216">21318</span><span class="sxs-lookup"><span data-stu-id="ca3ce-216">21318</span></span>|<span data-ttu-id="ca3ce-217">CLR 스칼라 함수</span><span class="sxs-lookup"><span data-stu-id="ca3ce-217">CLR Scalar Function</span></span>|  
|<span data-ttu-id="ca3ce-218">21321</span><span class="sxs-lookup"><span data-stu-id="ca3ce-218">21321</span></span>|<span data-ttu-id="ca3ce-219">인라인 스칼라 SQL 함수</span><span class="sxs-lookup"><span data-stu-id="ca3ce-219">Inline scalar SQL Function</span></span>|  
|<span data-ttu-id="ca3ce-220">21328</span><span class="sxs-lookup"><span data-stu-id="ca3ce-220">21328</span></span>|<span data-ttu-id="ca3ce-221">파티션 구성표</span><span class="sxs-lookup"><span data-stu-id="ca3ce-221">Partition Scheme</span></span>|  
|<span data-ttu-id="ca3ce-222">21333</span><span class="sxs-lookup"><span data-stu-id="ca3ce-222">21333</span></span>|<span data-ttu-id="ca3ce-223">사용자</span><span class="sxs-lookup"><span data-stu-id="ca3ce-223">User</span></span>|  
|<span data-ttu-id="ca3ce-224">21571</span><span class="sxs-lookup"><span data-stu-id="ca3ce-224">21571</span></span>|<span data-ttu-id="ca3ce-225">Service Broker 서비스 계약</span><span class="sxs-lookup"><span data-stu-id="ca3ce-225">Service Broker Service Contract</span></span>|  
|<span data-ttu-id="ca3ce-226">21572</span><span class="sxs-lookup"><span data-stu-id="ca3ce-226">21572</span></span>|<span data-ttu-id="ca3ce-227">데이터베이스에 대한 트리거</span><span class="sxs-lookup"><span data-stu-id="ca3ce-227">Trigger on Database</span></span>|  
|<span data-ttu-id="ca3ce-228">21574</span><span class="sxs-lookup"><span data-stu-id="ca3ce-228">21574</span></span>|<span data-ttu-id="ca3ce-229">CLR 테이블 반환 함수</span><span class="sxs-lookup"><span data-stu-id="ca3ce-229">CLR Table-valued Function</span></span>|  
|<span data-ttu-id="ca3ce-230">21577</span><span class="sxs-lookup"><span data-stu-id="ca3ce-230">21577</span></span>|<span data-ttu-id="ca3ce-231">내부 테이블(예: XML 노드 테이블, 큐 테이블)</span><span class="sxs-lookup"><span data-stu-id="ca3ce-231">Internal Table (For example, XML Node Table, Queue Table.)</span></span>|  
|<span data-ttu-id="ca3ce-232">21581</span><span class="sxs-lookup"><span data-stu-id="ca3ce-232">21581</span></span>|<span data-ttu-id="ca3ce-233">Service Broker 메시지 유형</span><span class="sxs-lookup"><span data-stu-id="ca3ce-233">Service Broker Message Type</span></span>|  
|<span data-ttu-id="ca3ce-234">21586</span><span class="sxs-lookup"><span data-stu-id="ca3ce-234">21586</span></span>|<span data-ttu-id="ca3ce-235">Service Broker 경로</span><span class="sxs-lookup"><span data-stu-id="ca3ce-235">Service Broker Route</span></span>|  
|<span data-ttu-id="ca3ce-236">21587</span><span class="sxs-lookup"><span data-stu-id="ca3ce-236">21587</span></span>|<span data-ttu-id="ca3ce-237">통계</span><span class="sxs-lookup"><span data-stu-id="ca3ce-237">Statistics</span></span>|  
|<span data-ttu-id="ca3ce-238">21825</span><span class="sxs-lookup"><span data-stu-id="ca3ce-238">21825</span></span><br /><br /> <span data-ttu-id="ca3ce-239">21827</span><span class="sxs-lookup"><span data-stu-id="ca3ce-239">21827</span></span><br /><br /> <span data-ttu-id="ca3ce-240">21831</span><span class="sxs-lookup"><span data-stu-id="ca3ce-240">21831</span></span><br /><br /> <span data-ttu-id="ca3ce-241">21843</span><span class="sxs-lookup"><span data-stu-id="ca3ce-241">21843</span></span><br /><br /> <span data-ttu-id="ca3ce-242">21847</span><span class="sxs-lookup"><span data-stu-id="ca3ce-242">21847</span></span>|<span data-ttu-id="ca3ce-243">사용자</span><span class="sxs-lookup"><span data-stu-id="ca3ce-243">User</span></span>|  
|<span data-ttu-id="ca3ce-244">22099</span><span class="sxs-lookup"><span data-stu-id="ca3ce-244">22099</span></span>|<span data-ttu-id="ca3ce-245">Service Broker 서비스</span><span class="sxs-lookup"><span data-stu-id="ca3ce-245">Service Broker Service</span></span>|  
|<span data-ttu-id="ca3ce-246">22601</span><span class="sxs-lookup"><span data-stu-id="ca3ce-246">22601</span></span>|<span data-ttu-id="ca3ce-247">인덱스</span><span class="sxs-lookup"><span data-stu-id="ca3ce-247">Index</span></span>|  
|<span data-ttu-id="ca3ce-248">22604</span><span class="sxs-lookup"><span data-stu-id="ca3ce-248">22604</span></span>|<span data-ttu-id="ca3ce-249">인증서 로그인</span><span class="sxs-lookup"><span data-stu-id="ca3ce-249">Certificate Login</span></span>|  
|<span data-ttu-id="ca3ce-250">22611</span><span class="sxs-lookup"><span data-stu-id="ca3ce-250">22611</span></span>|<span data-ttu-id="ca3ce-251">XMLSchema</span><span class="sxs-lookup"><span data-stu-id="ca3ce-251">XMLSchema</span></span>|  
|<span data-ttu-id="ca3ce-252">22868</span><span class="sxs-lookup"><span data-stu-id="ca3ce-252">22868</span></span>|<span data-ttu-id="ca3ce-253">Type</span><span class="sxs-lookup"><span data-stu-id="ca3ce-253">Type</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca3ce-254">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca3ce-254">See Also</span></span>  
 [<span data-ttu-id="ca3ce-255">sp_trace_setevent&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ca3ce-255">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
