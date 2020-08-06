---
title: 호환 되지 않는 데이터베이스 엔진 서버 데이터 정렬 (업그레이드 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b6ce0555bdf5a878e56d87a8bd55b5ce6c4b2649
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660296"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a><span data-ttu-id="baf93-102">호환되지 않는 데이터베이스 엔진 서버 데이터 정렬(업그레이드 관리자)</span><span class="sxs-lookup"><span data-stu-id="baf93-102">Incompatible Database Engine Server Collation (Upgrade Advisor)</span></span>
  <span data-ttu-id="baf93-103">업그레이드 관리자 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 호환 되지 않는 서버 데이터 정렬을 사용 하도록 구성 된의 인스턴스를 사용 하 고 있음을 발견 했습니다.</span><span class="sxs-lookup"><span data-stu-id="baf93-103">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is using an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that is configured to use an incompatible server collation.</span></span>  
  
||  
|-|  
|<span data-ttu-id="baf93-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint 모드.</span><span class="sxs-lookup"><span data-stu-id="baf93-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="baf93-105">구성 요소</span><span class="sxs-lookup"><span data-stu-id="baf93-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="baf93-106">Description</span><span class="sxs-lookup"><span data-stu-id="baf93-106">Description</span></span>  
 <span data-ttu-id="baf93-107">업그레이드 관리자 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 가 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 호환 되지 않는 서버 데이터 정렬을 사용 하도록 구성 된의 인스턴스를 사용 하 고 있음을 발견 했습니다.</span><span class="sxs-lookup"><span data-stu-id="baf93-107">Upgrade Advisor detected [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is using an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that is configured to use an incompatible server collation.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="baf93-108">Sharepoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 모드는 sharepoint 공유 서비스 아키텍처를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="baf93-108">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode utilizes the SharePoint shared services architecture.</span></span> <span data-ttu-id="baf93-109">SharePoint는 대/소문자를 구분하도록 구성된 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 또는 서버 데이터 정렬 또는 이진 서버 데이터 정렬을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="baf93-109">SharePoint does not support [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] configured for case sensitive or server collations or binary server collations.</span></span> <span data-ttu-id="baf93-110">호환되지 않는 데이터 정렬에는 기본적으로 대/소문자 구분되는 데이터 정렬 또는 기본적으로 호환되지만 다음 데이터 정렬 지정자 중 하나로 구성된 이진 및 기본 데이터 정렬을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="baf93-110">Incompatible collations include collations that are by default case sensitive or binary and a base collation that by default is compatible but has been configured with any of the following collation designators:</span></span>  
  
-   <span data-ttu-id="baf93-111">**이진**</span><span class="sxs-lookup"><span data-stu-id="baf93-111">**Binary**</span></span>  
  
-   <span data-ttu-id="baf93-112">**대/소문자 구분**</span><span class="sxs-lookup"><span data-stu-id="baf93-112">**Case-sensitive**</span></span>  
  
-   <span data-ttu-id="baf93-113">**이진 코드 포인트**</span><span class="sxs-lookup"><span data-stu-id="baf93-113">**Binary-codepoint**</span></span>  
  
 <span data-ttu-id="baf93-114">현재 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 서버 데이터 정렬은 호환되지 않으므로 업그레이드가 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="baf93-114">Because the current [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] server collation is incompatible, upgrade is blocked.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="baf93-115">수정 동작</span><span class="sxs-lookup"><span data-stu-id="baf93-115">Corrective Action</span></span>  
 <span data-ttu-id="baf93-116">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 서버 데이터 정렬 속성은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="baf93-116">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] server collation property cannot be changed.</span></span> <span data-ttu-id="baf93-117">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 업그레이드를 완료할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="baf93-117">You will not be able to complete an upgrade of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="baf93-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 설치를 호환되는 서버 데이터 정렬을 사용 중인 새 서버로 마이그레이션해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="baf93-118">You will need to migrate your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installation to a new server which is using a compatible server collation.</span></span> <span data-ttu-id="baf93-119">자세한 내용은</span><span class="sxs-lookup"><span data-stu-id="baf93-119">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="baf93-120">Reporting Services 업그레이드 및 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="baf93-120">Upgrade and Migrate Reporting Services</span></span>](https://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [<span data-ttu-id="baf93-121">SQL Server 데이터 정렬 선택</span><span class="sxs-lookup"><span data-stu-id="baf93-121">Selecting a SQL Server Collation</span></span>](https://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
