---
title: 기능 검토 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1e2b22b8-5811-4f50-875b-685f3ddbd1ee
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8e258ac763d8c5e057f8dcdb6f740aacb4fef1c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653177"
---
# <a name="feature-review"></a><span data-ttu-id="6e074-102">기능 검토</span><span class="sxs-lookup"><span data-stu-id="6e074-102">Feature Review</span></span>
  <span data-ttu-id="6e074-103">기능 검토 페이지는 현재 준비되어 있고 앞으로 구성되어 이미지 완료 단계의 끝에 완성될 여러 가지 기능이 포함된 읽기 전용 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-103">The Feature Review page is a read-only list of features that have been prepared and will be configured and completed at the end of the complete image step.</span></span> <span data-ttu-id="6e074-104">기능 목록은 이미지 준비 단계에서 선택되며 이미지 완료 단계에서는 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-104">The feature list is selected during the prepare image step and cannot be modified during complete image step.</span></span> <span data-ttu-id="6e074-105">준비 인스턴스에는 표시된 기능뿐만 아니라 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-105">In addition to the features displayed, a prepared instance also includes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Writer, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 <span data-ttu-id="6e074-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 준비 인스턴스 구성 작업을 완료한 후에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 준비 인스턴스에 포함되지 않은 다른 기능을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-106">You can add other features not included in the prepared instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance after you have completed the configuration of the prepared instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="6e074-107">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="6e074-107">UI element list</span></span>  
  
|<span data-ttu-id="6e074-108">구성 요소 그룹</span><span class="sxs-lookup"><span data-stu-id="6e074-108">Component Group</span></span>|<span data-ttu-id="6e074-109">구성 요소 및 기능</span><span class="sxs-lookup"><span data-stu-id="6e074-109">Components and features</span></span>|  
|---------------------|-----------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="6e074-110">서비스</span><span class="sxs-lookup"><span data-stu-id="6e074-110">Services</span></span>|<span data-ttu-id="6e074-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 은 데이터 저장, 처리 및 보안 유지를 위한 핵심 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-111">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] is the core service for storing, processing, and securing data.</span></span> <span data-ttu-id="6e074-112">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 의 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-112">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] includes the following components:</span></span><br /><br /> <span data-ttu-id="6e074-113">복제: (선택 사항) 복제는 한 데이터베이스에서 다른 데이터베이스로 데이터와 데이터베이스 개체를 복사 및 배포한 후 데이터베이스 간에 동기화를 수행하여 일관성을 유지하는 일련의 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-113">Replication: (Optional) Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency.</span></span><br /><br /> <span data-ttu-id="6e074-114">전체 텍스트 검색: (옵션) 전체 텍스트 검색에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블의 일반 문자 기반 데이터에 대해 전체 텍스트 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-114">Full-Text Search: (Optional) Full-Text Search provides functionality to issue full-text queries against plain character-based data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span><br /><br /> [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] <span data-ttu-id="6e074-115">(선택 사항): [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)](DQS)은(는) 데이터 원본에서 일관성 없고 올바르지 않은 데이터를 검색하는 데 사용할 수 있는 데이터 정리 솔루션으로, 자동화된 대화형 데이터 정리 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-115">(Optional): [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) is a data-cleansing solution that enables you to discover inconsistent and incorrect data in your data source, and provides automated and interactive ways to cleanse the data.</span></span>|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="6e074-116">에는 테이블 형식, 행렬, 그래픽 및 자유 형식 보고서를 생성, 관리 및 배포하기 위한 서버/클라이언트 구성 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-116">includes server and client components for creating, managing, and deploying tabular, matrix, graphical, and free-form reports.</span></span> <span data-ttu-id="6e074-117">또한[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 보고서 애플리케이션을 개발하는 데 사용할 수 있는 확장 가능 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="6e074-117">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is also an extensible platform that you can use to develop report applications.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e074-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e074-118">See Also</span></span>  
 [<span data-ttu-id="6e074-119">SysPrep을 사용하여 SQL Server 2014 설치</span><span class="sxs-lookup"><span data-stu-id="6e074-119">Install SQL Server 2014 Using SysPrep</span></span>](../../database-engine/install-windows/install-sql-server-using-sysprep.md)  
  
  
