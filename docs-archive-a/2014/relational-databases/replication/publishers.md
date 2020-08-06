---
title: 게시자 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.enablepublishers.f1
ms.assetid: 116cd6a5-32ac-4273-81a2-d184408e0f07
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 879fa3cc2ecadf56914928c6ae83600f513f6ddb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638646"
---
# <a name="publishers"></a><span data-ttu-id="7062b-102">게시자</span><span class="sxs-lookup"><span data-stu-id="7062b-102">Publishers</span></span>
  <span data-ttu-id="7062b-103">다른 게시자에 이 배포자를 사용하도록 사용 권한을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7062b-103">You can give permission for other Publishers to use this Distributor.</span></span> <span data-ttu-id="7062b-104">현재 서버를 원격 배포자로 사용하도록 게시자를 설정해도 해당 서버가 게시자가 되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7062b-104">Be aware that enabling a Publisher to use this server as its remote Distributor does not make that server a Publisher.</span></span> <span data-ttu-id="7062b-105">게시자에 연결하여 이를 게시자로 구성하고, 이 서버를 배포자로 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7062b-105">You must connect to the Publisher, configure it for publishing, and choose this server as the Distributor.</span></span> <span data-ttu-id="7062b-106">새 게시 마법사를 통해 게시자를 구성하고 배포자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7062b-106">You can configure the Publisher and choose a Distributor through the New Publication Wizard.</span></span>  
  
 <span data-ttu-id="7062b-107">게시자로 선택한 서버는 이 마법사의 **배포 데이터베이스** 페이지에서 지정한 배포 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7062b-107">The servers you select as Publishers will use the distribution database specified on the **Distribution Database** page of this wizard.</span></span> <span data-ttu-id="7062b-108">다른 배포 데이터베이스를 사용하려면 이때 게시자를 설정하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7062b-108">If you want to use a different distribution database, do not enable the Publisher at this time.</span></span> <span data-ttu-id="7062b-109">대신 배포 구성 마법사를 완료한 후 **배포자 속성** 대화 상자를 사용하여 게시자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7062b-109">Instead, use the **Distributor Properties** dialog box to add Publishers after you complete the Configure Distribution Wizard.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7062b-110">옵션</span><span class="sxs-lookup"><span data-stu-id="7062b-110">Options</span></span>  
 <span data-ttu-id="7062b-111">**게시자**</span><span class="sxs-lookup"><span data-stu-id="7062b-111">**Publishers**</span></span>  
 <span data-ttu-id="7062b-112">이 배포자를 사용하도록 허용할 서버를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="7062b-112">Select the servers that are allowed to use this Distributor.</span></span> <span data-ttu-id="7062b-113">게시자 옆의 속성 단추 ( **...** )를 클릭하여 추가 속성을 보고 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7062b-113">Click the properties button (**...**) next to a Publisher to view and set additional properties.</span></span>  
  
 <span data-ttu-id="7062b-114">**추가**</span><span class="sxs-lookup"><span data-stu-id="7062b-114">**Add**</span></span>  
 <span data-ttu-id="7062b-115">허용할 서버가 나열되지 않으면 **추가**를 클릭하여 사용 가능한 게시자 목록에 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자 또는 Oracle 게시자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7062b-115">If the server you want to allow is not listed, click **Add** to add a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Publisher or Oracle Publisher to the list of available Publishers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7062b-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7062b-116">See Also</span></span>  
 <span data-ttu-id="7062b-117">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="7062b-117">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="7062b-118">[게시 및 배포 구성](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="7062b-118">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="7062b-119">[배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="7062b-119">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="7062b-120">게시 만들기</span><span class="sxs-lookup"><span data-stu-id="7062b-120">Create a Publication</span></span>](publish/create-a-publication.md)  
  
  
