---
title: 구독자 속성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81ab9cf5f277ccfe1044e5a7083f019db9d843ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740804"
---
# <a name="subscriber-properties"></a><span data-ttu-id="5e8df-102">구독자 속성</span><span class="sxs-lookup"><span data-stu-id="5e8df-102">Subscriber Properties</span></span>
  <span data-ttu-id="5e8df-103">**구독자 속성** 대화 상자에는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 이전 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]를 실행 중인 구독자와 관련된 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e8df-103">The **Subscriber Properties** dialog box contains information relevant to Subscribers running versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="5e8df-104">옵션</span><span class="sxs-lookup"><span data-stu-id="5e8df-104">Options</span></span>  
 <span data-ttu-id="5e8df-105">**에이전트에서 구독자 연결**</span><span class="sxs-lookup"><span data-stu-id="5e8df-105">**Agent Connection to the Subscriber**</span></span>  
 <span data-ttu-id="5e8df-106">배포 에이전트 및 병합 에이전트가 배포자에서 구독자로 연결하는 컨텍스트로서, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]이전 버전에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e8df-106">The context under which the Distribution Agent and Merge Agent connect from the Distributor to the Subscriber This applies only to versions before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="5e8df-107">**에이전트 프로세스 계정 가장** 을 선택하여 배포자에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 계정의 컨텍스트를 사용하여 구독자에 연결하거나 **SQL Server 인증**을 지정한 다음 **로그인** 및 **암호**에 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5e8df-107">Select **Impersonate agent process account** to make connections to the Subscriber using the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent account at the Distributor, or specify **SQL Server Authentication**, and then enter a value for **Login** and **Password**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="5e8df-108">에서는 **에이전트 프로세스 계정 가장**을 선택할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="5e8df-108">recommends that you select **Impersonate agent process account**.</span></span>  
  
 <span data-ttu-id="5e8df-109">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전의 경우 연결 정보는 새 구독 마법사에서 각 구독에 대해 지정되며 **구독 속성** 대화 상자에서 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e8df-109">For [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, connection information is specified for each subscription in the New Subscription Wizard and can be changed in the **Subscription Properties** dialog box.</span></span>  
  
 <span data-ttu-id="5e8df-110">**기본 에이전트 일정**</span><span class="sxs-lookup"><span data-stu-id="5e8df-110">**Default Agent Schedules**</span></span>  
 <span data-ttu-id="5e8df-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이전 버전의 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]를 실행 중인 구독자에 대해 새 구독 마법사에서 사용하는 기본 일정입니다.</span><span class="sxs-lookup"><span data-stu-id="5e8df-111">The default schedule used in the New Subscription Wizard for Subscribers running versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span>  
  
 <span data-ttu-id="5e8df-112">**기타**</span><span class="sxs-lookup"><span data-stu-id="5e8df-112">**Miscellaneous**</span></span>  
 <span data-ttu-id="5e8df-113">구독자 및 구독자 유형에 대한 정보를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5e8df-113">Includes information on the Subscriber and Subscriber type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e8df-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e8df-114">See Also</span></span>  
 [<span data-ttu-id="5e8df-115">배포자 및 게시자 속성 보기 및 수정</span><span class="sxs-lookup"><span data-stu-id="5e8df-115">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

 [<span data-ttu-id="5e8df-116">게시 구독</span><span class="sxs-lookup"><span data-stu-id="5e8df-116">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
