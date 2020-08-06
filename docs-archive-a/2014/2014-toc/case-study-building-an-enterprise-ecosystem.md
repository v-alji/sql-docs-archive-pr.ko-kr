---
title: '사례 연구: 확장성과 성능을 위해 Microsoft Dynamics ERP 및 SQL Server 2014 복제를 사용 하 여 엔터프라이즈 에코 시스템 구축 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 2b0b5ab7-4e08-431a-bd59-360177c4565c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: dfde59b5e3e12746aa6dbaf975b079cfe32a3718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639125"
---
# <a name="case-study-building-an-enterprise-ecosystem-with-microsoft-dynamics-erp-and-sql-server-2014-replication-for-scalability-and-performance"></a><span data-ttu-id="ad26a-102">사례 연구: 확장성과 성능을 위해 Microsoft Dynamics ERP와 SQL Server 2014 Replication을 사용하여 엔터프라이즈 에코시스템 구축</span><span class="sxs-lookup"><span data-stu-id="ad26a-102">Case Study: Building an Enterprise Ecosystem with Microsoft Dynamics ERP and SQL Server 2014 Replication for Scalability and Performance</span></span>

  <span data-ttu-id="ad26a-103">**요약:** 이 문서에서는 다음과 같은 시나리오를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-103">**Summary:** This paper covers the following scenarios:</span></span>  
<span data-ttu-id="ad26a-104">SQL Server 2014에서 트랜잭션 복제를 사용 하 여 여러 노드에 걸친 Dynamics AX 클라이언트의 트랜잭션을 분산 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-104">How to use transactional replication in SQL Server 2014 to distribute the transactions from Dynamics AX clients across multiple nodes.</span></span> <span data-ttu-id="ad26a-105">데이터가 전체 노드에서 실시간으로 유지 관리되므로 트랜잭션 복제에서 데이터 중복성을 제공하여 데이터 가용성을 늘리고 더 효율적인 성능 분석에 사용할 수 있는 데이터를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-105">Because data is maintained across the nodes in real-time, transactional replication provides data redundancy, which increases the availability of data, includes data available for more efficient performance analysis.</span></span>  
<span data-ttu-id="ad26a-106">Microsoft Dynamics ERP에서 트래잭션 복제를 활용하여 확장성이 뛰어난 엔터프라이즈 에코시스템을 구축할 때 관련된 세부 사항을 이해하는 방법.</span><span class="sxs-lookup"><span data-stu-id="ad26a-106">How to understand the specifics involved while leveraging transactional replication to build highly scalable Enterprise ecosystems in Microsoft Dynamics ERP.</span></span> <span data-ttu-id="ad26a-107">AX의 기본 기능을 사용자 지정하지 않고도 고성능과 확장성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-107">Deliver high performance and scalability without customizing the AX out-of-box features.</span></span>  
  
 <span data-ttu-id="ad26a-108">일반적으로 트랜잭션 복제는 높은 처리량이 필요한 서버 간 워크플로에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-108">Transactional replication is typically used in server-to-server workflows that require high throughput.</span></span> <span data-ttu-id="ad26a-109">이러한 시나리오의 예로 확장성 및 가용성 향상, 데이터 웨어하우징 및 보고, 여러 사이트의 데이터 통합, 다른 유형의 데이터 통합, 일괄 처리 작업 오프로드 등을 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-109">These include scenarios, such as improving scalability and availability, data warehousing and reporting, integrating data from multiple sites, integrating heterogeneous data, and offloading batch processing.</span></span> <span data-ttu-id="ad26a-110">이 백서에서는 Microsoft Dynamics ERP에서 트랜잭션 복제를 활용하는 고유한 시나리오 및 관련 패턴을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-110">This white paper describes a distinct scenario and associated patterns where transactional replication is leveraged in Microsoft Dynamics ERP.</span></span> <span data-ttu-id="ad26a-111">또한 ERP(엔터프라이즈 리소스 계획) 관련 엔터프라이즈 솔루션을 구축하기 위해 트랜잭션 복제를 고려할 경우의 문제와 모범 사례 및 각 단계의 성능 분석에 대해서도 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-111">It also covers the challenges and best practices when considering transactional replication to build enterprise solutions specific to Enterprise Resource Planning (ERP), as well as the performance analysis at different stages.</span></span>  
  
 <span data-ttu-id="ad26a-112">이 콘텐츠는 개발자, 설계자 및 데이터베이스 관리자에게 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-112">This content is suitable for developers, architects, and database administrators.</span></span> <span data-ttu-id="ad26a-113">여기서는 이 백서의 독자가 SQL Server 관리 환경뿐만 아니라 SQL Server 2008, 2012 또는 2014에 대한 기본 지식이 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-113">It is assumed that readers of this white paper have basic knowledge of SQL Server 2008, 2012, or 2014 as well as SQL Server administration experience.</span></span>  
  
 <span data-ttu-id="ad26a-114">**기록기:** Prabhakaran Sethuraman (PRAB), Microsoft</span><span class="sxs-lookup"><span data-stu-id="ad26a-114">**Writer:** Prabhakaran Sethuraman (PRAB), Microsoft</span></span>  
  
 <span data-ttu-id="ad26a-115">**기술 검토자:** Prabhakaran Sethuraman (PRAB), Microsoft, Santosh가 Padhy, Microsoft, Pavel Majstrov, Microsoft, Karthik Sankaranarayanan, Microsoft, Jon Acone, Microsoft, David Stahlkopf, Microsoft, Kent Oldenburger, Microsoft, Ohlinger; Microsoft; Jason Roth, Microsoft</span><span class="sxs-lookup"><span data-stu-id="ad26a-115">**Technical Reviewers:** Prabhakaran Sethuraman (PRAB), Microsoft; Santosh Padhy, Microsoft; Pavel Majstrov, Microsoft; Karthik Sankaranarayanan, Microsoft; Jon Acone, Microsoft; David Stahlkopf, Microsoft;Kent Oldenburger, Microsoft; Mandi Ohlinger, Microsoft; Jason Roth, Microsoft</span></span>  
  
 <span data-ttu-id="ad26a-116">**게시 됨:** 10 월 2015</span><span class="sxs-lookup"><span data-stu-id="ad26a-116">**Published:** October 2015</span></span>  
  
 <span data-ttu-id="ad26a-117">**적용 대상:** SQL Server 2008, SQL Server 2012 및 SQL Server 2014</span><span class="sxs-lookup"><span data-stu-id="ad26a-117">**Applies to:** SQL Server 2008, SQL Server 2012, and SQL Server 2014</span></span>  
  
 <span data-ttu-id="ad26a-118">문서를 검토 하려면 다음을 다운로드 하세요.</span><span class="sxs-lookup"><span data-stu-id="ad26a-118">To review the document, please download the</span></span>  
        <span data-ttu-id="ad26a-119">[사례 연구: 확장성 및 성능을 위해 Microsoft DYNAMICS ERP 및 SQL Server 2014 복제를 사용 하 여 엔터프라이즈 에코 시스템 구축](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx) Word 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="ad26a-119">[Case Study: Building an Enterprise Ecosystem with Microsoft Dynamics ERP and SQL Server 2014 Replication for Scalability and Performance](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/A%20Case%20Study%20Using%20Replication%20to%20Build%20an%20Enterprise%20Ecosystem%20in%20Microsoft%20Dynamics%20ERP%20for%20Scalability%20and%20Performance.docx) Word document.</span></span>  
  
  
