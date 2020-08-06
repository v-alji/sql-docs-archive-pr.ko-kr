---
title: 데이터베이스 수명 주기 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Data sync
- SQL Database
- Azure Training Kit
- Database development
- Database backup
- Database connection management
- Database community
- Backup and restore
- Database import and export
- SQL Data Sync
- Azure Service Dashboard
- SQL Server Management Studio
- Database management
- Database export
- SQL Server Data Tools
- SSMS
- SSDT
- Database migration
- Database connectivity
ms.assetid: 91da13a4-0eea-4e88-b608-dada881ff5f2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a2c469b23e1ce4134767920547297b23ec030cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659453"
---
# <a name="database-lifecycle-management"></a><span data-ttu-id="474be-102">데이터베이스 수명 주기 관리</span><span class="sxs-lookup"><span data-stu-id="474be-102">Database Lifecycle Management</span></span>
  <span data-ttu-id="474be-103">DLM(데이터베이스 수명 주기 관리)은 정책을 기반으로 하는 데이터베이스 및 데이터 자산 관리 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="474be-103">Database lifecycle management (DLM) is a policy-based approach to managing databases and data assets.</span></span> <span data-ttu-id="474be-104">DLM은 제품이 아니지만 데이터베이스 애플리케이션의 데이터베이스 스키마, 데이터 및 메타데이터를 관리하는 포괄적인 접근 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="474be-104">DLM is not a product but a comprehensive approach to managing the database schema, data, and metadata for a database application.</span></span> <span data-ttu-id="474be-105">DLM에 대한 신중한 사전 접근 방식을 통해 조직에서는 적절한 수준의 성능, 보고, 가용성 및 비용에 따라 데이터 리소스를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="474be-105">A thoughtful and proactive approach to DLM enables an organization to manage data resources according to appropriate levels of performance, protection, availability, and cost.</span></span>  
  
 <span data-ttu-id="474be-106">DLM은 프로젝트 디자인과 의도에 대한 논의로 시작하여, 데이터베이스 개발, 테스트, 빌드, 배포, 유지 관리, 모니터링 및 백업 작업으로 이어지고, 데이터베이스 보관으로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="474be-106">DLM begins with discussion of project design and intent, continues with database develop, test, build, deploy, maintain, monitor, and backup activities, and ends with data archive.</span></span> <span data-ttu-id="474be-107">이 항목에서는 데이터베이스 개발로 시작하여 빌드, 배포 및 모니터링 작업으로 이어지는 DLM의 단계를 간략하게 설명합니다(그림 1).</span><span class="sxs-lookup"><span data-stu-id="474be-107">This topic provides an overview of the stages of DLM that begin with database development and progress through build, deploy, and monitor actions (Figure 1).</span></span> <span data-ttu-id="474be-108">여기에는 데이터베이스 관리 작업과 가져오기/내보내기, 백업, 마이그레이션, 동기화 등의 데이터 이식성 작업도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="474be-108">Also included are data management activities, and data portability operations like import/export, backup, migrate, and sync.</span></span>  
  
 <span data-ttu-id="474be-109">전체 항목을 읽으려면 [DLM(데이터베이스 수명 주기 관리)](https://go.microsoft.com/fwlink/?LinkId=276949)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="474be-109">To read the complete topic, see [Database Lifecycle Management (DLM)](https://go.microsoft.com/fwlink/?LinkId=276949).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="474be-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="474be-110">See Also</span></span>  
 <span data-ttu-id="474be-111">[Azure 홈 페이지](https://www.windowsazure.com/) </span><span class="sxs-lookup"><span data-stu-id="474be-111">[Azure Home Page](https://www.windowsazure.com/) </span></span>  
 <span data-ttu-id="474be-112">[Azure 개발자 센터](https://www.windowsazure.com/develop/overview/) </span><span class="sxs-lookup"><span data-stu-id="474be-112">[Azure Developer Center](https://www.windowsazure.com/develop/overview/) </span></span>  
 <span data-ttu-id="474be-113">[Azure 관리 센터](https://www.windowsazure.com/manage/overview/) </span><span class="sxs-lookup"><span data-stu-id="474be-113">[Azure Manage Center](https://www.windowsazure.com/manage/overview/) </span></span>  
 <span data-ttu-id="474be-114">[Azure 팀 블로그](https://www.windowsazure.com/community/blog/) </span><span class="sxs-lookup"><span data-stu-id="474be-114">[Azure Team Blog](https://www.windowsazure.com/community/blog/) </span></span>  
 [<span data-ttu-id="474be-115">Azure 지원 옵션</span><span class="sxs-lookup"><span data-stu-id="474be-115">Azure Support Options</span></span>](https://www.windowsazure.com/support/contact/)  
  
