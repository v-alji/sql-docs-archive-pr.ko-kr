---
title: 클러스터 디스크 선택 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0f53d6d3f623254d2b17996be7fd5b8235dca223
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650502"
---
# <a name="cluster-disk-selection"></a><span data-ttu-id="99edd-102">클러스터 디스크 선택</span><span class="sxs-lookup"><span data-stu-id="99edd-102">Cluster Disk Selection</span></span>
  <span data-ttu-id="99edd-103">**설치 마법사의** 클러스터 디스크 선택 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 페이지를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 장애 조치(failover) 클러스터를 위한 공유 클러스터 디스크 리소스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-103">Use the **Cluster Disk Selection** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard to select the shared cluster disk resource for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster.</span></span> <span data-ttu-id="99edd-104">클러스터 디스크에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-104">The cluster disk is where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data will be placed.</span></span>  
  
 <span data-ttu-id="99edd-105">공유 클러스터 디스크는 클러스터 설치를 위한 요구 사항이 아닙니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="99edd-105">A shared cluster disk is not a requirement for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] cluster installations.</span></span> <span data-ttu-id="99edd-106">SMB 파일 서버는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 장애 조치 (failover) 클러스터 설치에 지원 되는 저장소로, 설치를 완료 하기 전에 **데이터베이스 엔진-데이터 디렉터리** 페이지를 사용 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-106">An SMB file server is a supported storage for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../../includes/ssde-md.md)] failover cluster installations, and can be specified by using the **Database Engine - Data Directories** page before completing the installation.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="99edd-107">Analysis Services를 설치하도록 선택한 경우 공유 클러스터 디스크를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-107">If you have selected Analysis Services to be installed, you must specify a shared cluster disk.</span></span>  
>   
>  <span data-ttu-id="99edd-108">이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]장애 조치(failover) 클러스터 인스턴스에서 FILESTREAM을 사용하려면 공유 클러스터 디스크를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-108">If you plan to enable FILESTREAM on this [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance, you must specify a shared cluster disk.</span></span>  
  
## <a name="options"></a><span data-ttu-id="99edd-109">옵션</span><span class="sxs-lookup"><span data-stu-id="99edd-109">Options</span></span>  
 <span data-ttu-id="99edd-110">**공유 디스크**</span><span class="sxs-lookup"><span data-stu-id="99edd-110">**Shared Disks**</span></span>  
 <span data-ttu-id="99edd-111">목록에서 단일 디스크를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-111">Select a single disk from the list.</span></span> <span data-ttu-id="99edd-112">클러스터 디스크에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-112">The cluster disk is where the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data will be placed.</span></span>  
  
 <span data-ttu-id="99edd-113">하나의 디스크만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-113">Only one disk can be specified.</span></span> <span data-ttu-id="99edd-114">클러스터 쿼럼 리소스가 있는 그룹을 선택할 경우 경고가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-114">If you select the group containing the cluster quorum resource, a warning will be displayed.</span></span> <span data-ttu-id="99edd-115">클러스터 쿼럼 리소스에 설치하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-115">We recommend that you do not install to the cluster quorum resource.</span></span>  
  
 <span data-ttu-id="99edd-116">**사용 가능한 공유 디스크**</span><span class="sxs-lookup"><span data-stu-id="99edd-116">**Available Shared Disks**</span></span>  
 <span data-ttu-id="99edd-117">사용 가능한 디스크 목록, 각 디스크가 공유 디스크로 정규화되었는지 여부 및 각 디스크 리소스에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="99edd-117">Displays a list of available disks, whether each is qualified as a shared disk, and a description of each disk resource.</span></span>  
  
  
