---
title: 유지 관리 계획(서버) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.maintplanproperties.server.f1
- sql12.swb.maint.servers.f1
ms.assetid: ac24d1a8-dd2f-4162-b804-c0df1fc1e61d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c971edc9b641846068313f47ca410715ec552014
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649522"
---
# <a name="maintenance-plan-servers"></a><span data-ttu-id="c1dfd-102">유지 관리 계획(서버)</span><span class="sxs-lookup"><span data-stu-id="c1dfd-102">Maintenance Plan (Servers)</span></span>
  <span data-ttu-id="c1dfd-103">**서버** 대화 상자를 사용하여 유지 관리 계획을 실행할 서버를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-103">Use the **Servers** dialog box to select the servers where you want to run the maintenance plan.</span></span>  
  
 <span data-ttu-id="c1dfd-104">하나의 마스터 서버 및 하나 이상의 대상 서버가 있는 다중 서버 환경은 다중 서버 유지 관리 계획을 만들도록 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-104">A multiserver environment containing one master server and one or more target servers must be configured to create a multiserver maintenance plan.</span></span> <span data-ttu-id="c1dfd-105">다중 서버 유지 관리 계획의 경우 로컬 서버를 마스터 서버로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-105">For multiserver maintenance plans, the local server should be configured as a master server.</span></span> <span data-ttu-id="c1dfd-106">다중 서버 환경에서 이 대화 상자에는 **(로컬)** 마스터 서버와 해당하는 모든 대상 서버가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-106">In multiserver environments, this dialog box displays the **(local)** master server and all corresponding target servers.</span></span> <span data-ttu-id="c1dfd-107">로컬 서버당 하나의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 작업이 생성되며</span><span class="sxs-lookup"><span data-stu-id="c1dfd-107">One [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job is created for the local server.</span></span> <span data-ttu-id="c1dfd-108">이러한 작업은 **(로컬)** 서버의 선택 여부에 따라 수행 또는 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-108">It is enabled or disabled depending on whether you select the **(local)** server.</span></span> <span data-ttu-id="c1dfd-109">대상 서버를 선택하면 다중 서버 작업이 생성되고 선택한 각 대상 서버에 다운로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-109">If target servers are selected, a multiserver job is created and downloaded to each of the selected target servers.</span></span> <span data-ttu-id="c1dfd-110">대상 서버를 선택하지 않으면 다중 서버 작업이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1dfd-110">If no target servers are selected, the multiserver job is deleted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1dfd-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1dfd-111">See Also</span></span>  
 <span data-ttu-id="c1dfd-112">[유지 관리 계획](maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="c1dfd-112">[Maintenance Plans](maintenance-plans.md) </span></span>  
 <span data-ttu-id="c1dfd-113">[다중 서버 환경 만들기](../../ssms/agent/create-a-multiserver-environment.md) </span><span class="sxs-lookup"><span data-stu-id="c1dfd-113">[Create a Multiserver Environment](../../ssms/agent/create-a-multiserver-environment.md) </span></span>  
 <span data-ttu-id="c1dfd-114">[마스터 서버 만들기](../../ssms/agent/make-a-master-server.md) </span><span class="sxs-lookup"><span data-stu-id="c1dfd-114">[Make a Master Server](../../ssms/agent/make-a-master-server.md) </span></span>  
 [<span data-ttu-id="c1dfd-115">대상 서버 만들기</span><span class="sxs-lookup"><span data-stu-id="c1dfd-115">Make a Target Server</span></span>](../../ssms/agent/make-a-target-server.md)  
  
  
