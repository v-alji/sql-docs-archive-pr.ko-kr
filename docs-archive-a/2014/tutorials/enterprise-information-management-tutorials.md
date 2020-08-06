---
title: 엔터프라이즈 정보 관리 자습서 | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8745dc80-193d-4de0-9f17-ba648ab1e81c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b8cde162479645ab13a6ae000cc46e42e3c10e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653079"
---
# <a name="enterprise-information-management-tutorials"></a><span data-ttu-id="09d94-102">엔터프라이즈 정보 관리 자습서</span><span class="sxs-lookup"><span data-stu-id="09d94-102">Enterprise Information Management Tutorials</span></span>
  <span data-ttu-id="09d94-103">이 단원에는 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]에 포함된 EIM(엔터프라이즈 정보 관리) 기술을 사용해서 기업에서 정보를 관리하기 위한 자습서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09d94-103">This section contains tutorials for managing information in an enterprise by using Enterprise Information Management (EIM) technologies that are included in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="09d94-104">EIM(엔터프라이즈 통합 관리)은 조직이 중요한 비즈니스 의사 결정을 내릴 수 있도록 데이터의 진실성 및 일관성을 신뢰할 수 있게 해주는 솔루션 포트폴리오를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="09d94-104">Enterprise Integration Management (EIM) provides a portfolio of solutions that enable organizations to trust the credibility and consistency of their data so they can make critical business decisions.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<span data-ttu-id="09d94-105">에는 기업 환경에 EIM 솔루션을 구현할 수 있도록 도와주는 다음과 같은 기술이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09d94-105">has the following technologies that help you implement EIM solutions in your enterprise.</span></span>  
  
-   <span data-ttu-id="09d94-106">SSIS(SQL Server Integration Services).</span><span class="sxs-lookup"><span data-stu-id="09d94-106">SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="09d94-107">SSIS는 다양한 원본의 데이터를 비즈니스 워크플로, 데이터 웨어하우스 또는 마스터 데이터 관리가 지원되는 포괄적인 ETL(추출, 변환 및 로드) 솔루션으로 통합하기 위한 강력하고 확장 가능한 플랫폼을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="09d94-107">SSIS provides a powerful, extensible platform for integrating data from various sources in a comprehensive extract, transform, and load (ETL) solution that supports business workflows, a data warehouse, or master data management.</span></span>  
  
-   <span data-ttu-id="09d94-108">SQL Server DQS(Data Quality Services).</span><span class="sxs-lookup"><span data-stu-id="09d94-108">SQL Server Data Quality Services (DQS).</span></span> <span data-ttu-id="09d94-109">DQS를 사용하면 비즈니스 인텔리전스, 데이터 웨어하우스 및 트랜잭션 처리 작업을 위해 신뢰할 수 있는 정보를 제공할 수 있도록 데이터를 정리, 일치, 표준화 및 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09d94-109">DQS enables you to cleanse, match, standardize, and enrich data, so you can deliver trusted information for business intelligence, a data warehouse, and transaction processing workloads.</span></span>  
  
-   <span data-ttu-id="09d94-110">SQL Server MDS(Master Data Services).</span><span class="sxs-lookup"><span data-stu-id="09d94-110">SQL Server Master Data Services (MDS).</span></span> <span data-ttu-id="09d94-111">MDS는 정보 무결성 및 데이터 일관성이 여러 애플리케이션 간에 일관되게 유지되도록 보장하는 중앙 데이터 허브를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="09d94-111">MDS provides a central data hub that ensures that the integrity of information and consistency of data is constant across different applications.</span></span>  
  
 [<span data-ttu-id="09d94-112">SSIS, MDS 및 DQS를 함께 사용 하는 엔터프라이즈 정보 관리 &#91;자습서&#93;</span><span class="sxs-lookup"><span data-stu-id="09d94-112">Enterprise Information Management using SSIS, MDS, and DQS Together &#91;Tutorial&#93;</span></span>](../../2014/tutorials/enterprise-information-management-using-ssis-mds-and-dqs-together-[tutorial].md)  
 <span data-ttu-id="09d94-113">이 자습서에서는 SSIS, MDS 및 DQS 기술을 함께 활용해서 예제 EIM(엔터프라이즈 정보 관리) 솔루션을 구현하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="09d94-113">In this tutorial, you learn how to use SSIS, MDS, and DQS together to implement a sample Enterprise Information Management (EIM) solution.</span></span> <span data-ttu-id="09d94-114">먼저, DQS를 사용해서 공급자 데이터(메타데이터)에 대한 지식이 포함된 기술 자료를 만들고, 기술 자료를 기반으로 Excel 파일에서 데이터를 정리하고, 데이터 일치를 통해 데이터에 있는 중복 항목을 식별 및 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="09d94-114">First, you use DQS to create a knowledgebase with the knowledge about the supplier data (metadata), cleanse the data in an Excel file against the knowledge base, and match the data to identify and remove duplicates in the data.</span></span> <span data-ttu-id="09d94-115">그런 다음 Excel용 MDS 추가 기능을 사용해서 정리되고 일치된 데이터를 MDS에 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="09d94-115">Next, you use the MDS Add-in for Excel to upload the cleansed and matched data to MDS.</span></span> <span data-ttu-id="09d94-116">마지막으로 SSIS 솔루션을 사용해서 전체 프로세스를 자동화합니다.</span><span class="sxs-lookup"><span data-stu-id="09d94-116">Then, you automate the whole process by using an SSIS solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09d94-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="09d94-117">See Also</span></span>  
 [<span data-ttu-id="09d94-118">엔터프라이즈 정보 관리-Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="09d94-118">Enterprise Information Management - Microsoft SQL Server</span></span>](https://go.microsoft.com/fwlink/?LinkId=270871)  
  
  
