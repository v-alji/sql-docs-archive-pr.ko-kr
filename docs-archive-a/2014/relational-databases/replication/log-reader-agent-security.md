---
title: 로그 판독기 에이전트 보안 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.security.LRA.f1
helpviewer_keywords:
- Log Reader Agent Security dialog box
ms.assetid: d6981e74-ddb8-41b8-9ea1-56c2ece63b8a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4be41aa9135e20a334616b9cb9d76a773f8d0e9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739693"
---
# <a name="log-reader-agent-security"></a><span data-ttu-id="b49ac-102">로그 판독기 에이전트 보안</span><span class="sxs-lookup"><span data-stu-id="b49ac-102">Log Reader Agent Security</span></span>
  <span data-ttu-id="b49ac-103">**로그 판독기 에이전트 보안** 대화 상자에서 다음을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-103">The **Log Reader Agent Security** dialog box allows you to specify:</span></span>  
  
-   <span data-ttu-id="b49ac-104">배포자에서 로그 판독기 에이전트를 실행하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정.</span><span class="sxs-lookup"><span data-stu-id="b49ac-104">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the Log Reader Agent runs at the Distributor.</span></span> <span data-ttu-id="b49ac-105">Windows 계정으로 에이전트 프로세스가 실행되기 때문에 이 계정을 *프로세스 계정*이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-105">The Windows account is also referred to as the *process account*, because the agent process runs under this account.</span></span>  
  
-   <span data-ttu-id="b49ac-106">로그 판독기 에이전트를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자에 연결하는 컨텍스트.</span><span class="sxs-lookup"><span data-stu-id="b49ac-106">The context under which the Log Reader Agent makes connections to the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher.</span></span> <span data-ttu-id="b49ac-107">Windows 계정을 가장하거나 지정한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정의 컨텍스트에서 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-107">The connection can be made by impersonating the Windows account or under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account you specify.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b49ac-108">게시자 및 배포자가 동일한 컴퓨터에 있는 경우에도 로그 판독기 에이전트를 게시자에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-108">The Log Reader Agent makes connections to the Publisher even if the Publisher and Distributor are on the same computer.</span></span> <span data-ttu-id="b49ac-109">또한 로그 판독기 에이전트를 배포자에 연결하며 이러한 연결은 항상 에이전트를 실행하는 Windows 계정을 가장하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-109">The Log Reader Agent also makes connections to the Distributor; these connections are always made by impersonating the Windows account under which the agent runs.</span></span>  
  
     <span data-ttu-id="b49ac-110">Oracle 게시자의 경우 **배포자 속성** 대화 상자에서 사용할 수 있는 **게시자 속성** 대화 상자에서 로그 판독기 에이전트를 게시자에 연결하는 컨텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-110">For Oracle Publishers, specify the context under which the Log Reader Agent connects to the Publisher in the **Publisher Properties** dialog box (available from the **Distributor Properties** dialog box).</span></span> <span data-ttu-id="b49ac-111">자세한 내용은 [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b49ac-111">For more information, see [View and Modify Replication Security Settings](security/view-and-modify-replication-security-settings.md).</span></span>  
  
 <span data-ttu-id="b49ac-112">모든 계정이 유효해야 하며 각 계정에 대해 올바른 암호를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-112">All accounts must be valid, with the correct password specified for each account.</span></span> <span data-ttu-id="b49ac-113">계정 및 암호의 유효성은 에이전트를 실행할 때 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-113">Accounts and passwords are not validated until an agent runs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b49ac-114">옵션</span><span class="sxs-lookup"><span data-stu-id="b49ac-114">Options</span></span>  
 <span data-ttu-id="b49ac-115">**프로세스 계정**</span><span class="sxs-lookup"><span data-stu-id="b49ac-115">**Process account**</span></span>  
 <span data-ttu-id="b49ac-116">배포자에서 로그 판독기 에이전트를 실행하는 Windows 계정을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-116">Enter a Windows account under which the Log Reader Agent runs at the Distributor.</span></span> <span data-ttu-id="b49ac-117">지정한 Windows 계정은 적어도 배포 데이터베이스에 포함된 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-117">The Windows account you specify must at minimum be a member of the **db_owner** fixed database role in the distribution database.</span></span>  
  
 <span data-ttu-id="b49ac-118">**암호** 및 **암호 확인**</span><span class="sxs-lookup"><span data-stu-id="b49ac-118">**Password** and **Confirm password**</span></span>  
 <span data-ttu-id="b49ac-119">Windows 계정의 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-119">Enter the password for the Windows account.</span></span>  
  
 <span data-ttu-id="b49ac-120">**게시자에 연결**</span><span class="sxs-lookup"><span data-stu-id="b49ac-120">**Connect to the Publisher**</span></span>  
 <span data-ttu-id="b49ac-121">로그 판독기 에이전트를 게시자에 연결할 때 **프로세스 계정** 입력란에 지정한 계정을 가장할지, 아니면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용할지를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-121">Select whether the Log Reader Agent should make connections to the Publisher by impersonating the account specified in the **Process account** text box or by using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span> <span data-ttu-id="b49ac-122">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하도록 선택한 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인과 암호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-122">If you select to use a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account, enter a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login and password.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="b49ac-123">에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정을 사용하는 대신 Windows 계정을 가장하도록 선택할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-123">recommends that you select to impersonate the Windows account rather than using a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account.</span></span>  
  
 <span data-ttu-id="b49ac-124">연결에 사용되는 Windows 계정이나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 계정은 적어도 게시 데이터베이스에 포함된 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b49ac-124">The Windows account or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account used for the connection must at minimum be a member of the **db_owner** fixed database role in the publication database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b49ac-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b49ac-125">See Also</span></span>  
 <span data-ttu-id="b49ac-126">[복제의 로그인 및 암호 관리](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="b49ac-126">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="b49ac-127">[복제 에이전트 보안 모델](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="b49ac-127">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 <span data-ttu-id="b49ac-128">[복제 에이전트 개요](agents/replication-agents-overview.md) </span><span class="sxs-lookup"><span data-stu-id="b49ac-128">[Replication Agents Overview](agents/replication-agents-overview.md) </span></span>  
 [<span data-ttu-id="b49ac-129">복제 보안을 위한 최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="b49ac-129">Replication Security Best Practices</span></span>](security/replication-security-best-practices.md)  
  
  
