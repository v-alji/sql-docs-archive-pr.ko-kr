---
title: WMI 오류 0x8007052f | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d6e857e0ccaad9b6f34bbdc9b88aea2e6d7291d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743116"
---
# <a name="wmi-error-0x8007052f"></a><span data-ttu-id="04b40-102">WMI 오류 0x8007052f</span><span class="sxs-lookup"><span data-stu-id="04b40-102">WMI Error 0x8007052f</span></span>
    
## <a name="details"></a><span data-ttu-id="04b40-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="04b40-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="04b40-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="04b40-104">Product Name</span></span>|<span data-ttu-id="04b40-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="04b40-105">SQL Server</span></span>|  
|<span data-ttu-id="04b40-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="04b40-106">Event ID</span></span>|<span data-ttu-id="04b40-107">0x8007052f</span><span class="sxs-lookup"><span data-stu-id="04b40-107">0x8007052f</span></span>|  
|<span data-ttu-id="04b40-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="04b40-108">Event Source</span></span>|<span data-ttu-id="04b40-109">WMI 공급자 오류</span><span class="sxs-lookup"><span data-stu-id="04b40-109">WMI Provider Error</span></span>|  
|<span data-ttu-id="04b40-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="04b40-110">Component</span></span>|<span data-ttu-id="04b40-111">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="04b40-111">SQL Server Configuration Manager</span></span>|  
|<span data-ttu-id="04b40-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="04b40-112">Symbolic Name</span></span>|<span data-ttu-id="04b40-113">해당 없음</span><span class="sxs-lookup"><span data-stu-id="04b40-113">NA</span></span>|  
|<span data-ttu-id="04b40-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="04b40-114">Message Text</span></span>|<span data-ttu-id="04b40-115">로그온 실패: 사용자 계정 제한입니다.</span><span class="sxs-lookup"><span data-stu-id="04b40-115">Logon failure: user account restriction.</span></span> <span data-ttu-id="04b40-116">빈 암호 사용, 로그온 시간 제한 또는 정책 제한으로 인해 이러한 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04b40-116">Possible reasons are blank passwords not allowed, login hour restrictions, or a policy restriction has been enforced.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="04b40-117">설명</span><span class="sxs-lookup"><span data-stu-id="04b40-117">Explanation</span></span>  
 <span data-ttu-id="04b40-118">이 오류는 Windows Server 클러스터 또는 Windows Server 도메인 컨트롤러에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가 실행 중일 때 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 네트워크 서비스, 로컬 서비스, 로컬 시스템과 같은 기본 제공 계정으로 전환할 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04b40-118">This error can occur when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager to switch to the built-in accounts (Network Service, Local Service, or Local System) when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running on a Windows Server Cluster or Windows Server Domain Controller.</span></span> <span data-ttu-id="04b40-119">Windows Server 클러스터 또는 Windows Server 도메인 컨트롤러에서는 기본 제공 계정으로 서비스를 실행하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="04b40-119">Do not run services under built-in accounts on a Windows Server Cluster or Windows Server Domain Controller.</span></span> <span data-ttu-id="04b40-120">서비스 계정에 대한 권장 사항은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 온라인 설명서의 “Windows 서비스 계정 설정” 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="04b40-120">For recommendations on service accounts, see the topic Setting Up Windows Service Accounts in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="04b40-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="04b40-121">User Action</span></span>  
 <span data-ttu-id="04b40-122">도메인 계정을 사용하도록 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="04b40-122">Configure [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to use a domain account.</span></span>  
  
  
