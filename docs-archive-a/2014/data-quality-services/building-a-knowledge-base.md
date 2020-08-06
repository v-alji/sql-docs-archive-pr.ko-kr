---
title: 기술 자료 구축 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 51eff161-6ecd-4ee4-8187-1dd8ef4814bd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 03c9fc6c3a9168a66e8293c61db21a87fadc260f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647267"
---
# <a name="building-a-knowledge-base"></a><span data-ttu-id="5cffd-102">기술 자료 구축</span><span class="sxs-lookup"><span data-stu-id="5cffd-102">Building a Knowledge Base</span></span>
  <span data-ttu-id="5cffd-103">DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )의 기술 자료는 데이터 관련 정보의 리포지토리로서 데이터를 이해하고 데이터의 무결성을 유지하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-103">A knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) is a repository of knowledge about your data that enables you to understand your data and maintain its integrity.</span></span> <span data-ttu-id="5cffd-104">기술 자료는 데이터 필드의 데이터를 나타내는 각각의 도메인으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-104">A knowledge base consists of domains, each of which represents the data in a data field.</span></span> <span data-ttu-id="5cffd-105">기술 자료는 DQS에서 데이터베이스에 대해 데이터 정리 및 중복 제거를 수행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-105">The knowledge base is used by DQS to perform data cleansing and deduplication on a database.</span></span> <span data-ttu-id="5cffd-106">데이터 정리를 위해 기술 자료를 준비하려면 데이터 샘플에 대한 컴퓨터 기반 분석을 실행하고 도메인의 값을 대화식으로 관리하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-106">To prepare the knowledge base for data cleansing, you can run a computer-assisted analysis of a data sample, and interactively manage values in the domains.</span></span> <span data-ttu-id="5cffd-107">DQS를 통해 정보를 가져오고, 규칙 및 관계를 만들고, 데이터 값을 직접 변경하고, 기본 데이터베이스를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-107">DQS enables you to import knowledge, create rules and relationships, change data values directly, and leverage a default database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5cffd-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="5cffd-108">In This Section</span></span>  
 <span data-ttu-id="5cffd-109">기술 자료에 대해 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-109">You can perform the following operations on a knowledge base:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5cffd-110">새 기술 자료를 처음부터 만들거나, 기존 기술 자료나 .dqs 데이터 파일을 통해 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-110">Create a new knowledge base from scratch, from an existing knowledge base, or from a .dqs data file.</span></span>|[<span data-ttu-id="5cffd-111">기술 자료 만들기</span><span class="sxs-lookup"><span data-stu-id="5cffd-111">Create a Knowledge Base</span></span>](../../2014/data-quality-services/create-a-knowledge-base.md)|  
|<span data-ttu-id="5cffd-112">기존 기술 자료를 열어 기술 자료 검색, 도메인 관리를 수행하거나 일치 정책을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-112">Open an existing knowledge base to perform knowledge discovery, domain management, or add a matching policy.</span></span>|[<span data-ttu-id="5cffd-113">기술 자료 열기</span><span class="sxs-lookup"><span data-stu-id="5cffd-113">Open a Knowledge Base</span></span>](../../2014/data-quality-services/open-a-knowledge-base.md)|  
|<span data-ttu-id="5cffd-114">기술 자료에 대해 열기, 잠금 해제, 관련 작업 취소, 이름 바꾸기, 삭제 또는 속성 보기 등의 관리 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-114">Perform management actions on a knowledge base, including opening it, unlocking it, discarding your work on it, renaming it, deleting it, or viewing its properties.</span></span>|[<span data-ttu-id="5cffd-115">기술 자료 관리</span><span class="sxs-lookup"><span data-stu-id="5cffd-115">Manage a Knowledge Base</span></span>](../../2014/data-quality-services/manage-a-knowledge-base.md)|  
|<span data-ttu-id="5cffd-116">기술 자료 검색, 도메인 값 관리, 일치 정책 추가, 정보/도메인/값 가져오기 또는 기본 기술 자료 DQS 데이터 사용을 통해 기술 자료에 정보를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-116">Add knowledge to a knowledge base through knowledge discovery; domain value management; adding a matching policy; importing a knowledge, domain, or values; or using the default knowledge base, DQS Data.</span></span>|[<span data-ttu-id="5cffd-117">기술 자료에 정보 추가</span><span class="sxs-lookup"><span data-stu-id="5cffd-117">Adding Knowledge to a Knowledge Base</span></span>](../../2014/data-quality-services/adding-knowledge-to-a-knowledge-base.md)|  
|<span data-ttu-id="5cffd-118">데이터 샘플이 데이터 품질 기준에 맞는지 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="5cffd-118">Analyze a data sample for data quality criteria.</span></span>|[<span data-ttu-id="5cffd-119">기술 자료 검색 수행</span><span class="sxs-lookup"><span data-stu-id="5cffd-119">Perform Knowledge Discovery</span></span>](../../2014/data-quality-services/perform-knowledge-discovery.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="5cffd-120">관련 작업</span><span class="sxs-lookup"><span data-stu-id="5cffd-120">Related Tasks</span></span>  
  
|<span data-ttu-id="5cffd-121">태스크 설명</span><span class="sxs-lookup"><span data-stu-id="5cffd-121">Task Description</span></span>|<span data-ttu-id="5cffd-122">항목</span><span class="sxs-lookup"><span data-stu-id="5cffd-122">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="5cffd-123">기술 자료로 정보 가져오기 또는 기술 자료에서 정보 내보내기</span><span class="sxs-lookup"><span data-stu-id="5cffd-123">Importing knowledge into, or exporting it from, a knowledge base.</span></span>|[<span data-ttu-id="5cffd-124">기술 자료 가져오기 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="5cffd-124">Importing and Exporting Knowledge</span></span>](../../2014/data-quality-services/importing-and-exporting-knowledge.md)|  
|<span data-ttu-id="5cffd-125">단일 도메인 만들기 및 단일 도메인에 정보 추가</span><span class="sxs-lookup"><span data-stu-id="5cffd-125">Creating a single domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="5cffd-126">도메인 관리</span><span class="sxs-lookup"><span data-stu-id="5cffd-126">Managing a Domain</span></span>](../../2014/data-quality-services/managing-a-domain.md)|  
|<span data-ttu-id="5cffd-127">복합 도메인 만들기 및 단일 도메인에 정보 추가</span><span class="sxs-lookup"><span data-stu-id="5cffd-127">Creating a composite domain, and adding knowledge to the domain.</span></span>|[<span data-ttu-id="5cffd-128">복합 도메인 관리</span><span class="sxs-lookup"><span data-stu-id="5cffd-128">Managing a Composite Domain</span></span>](../../2014/data-quality-services/managing-a-composite-domain.md)|  
  
  
