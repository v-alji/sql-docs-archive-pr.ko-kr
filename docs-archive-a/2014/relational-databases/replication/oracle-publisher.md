---
title: Oracle 게시자 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.selectoraclepublisher.f1
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db52b93b3d260ff58a151e7238bbbe065bc47bc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646347"
---
# <a name="oracle-publisher"></a><span data-ttu-id="2c0c3-102">Oracle 게시자</span><span class="sxs-lookup"><span data-stu-id="2c0c3-102">Oracle Publisher</span></span>
  <span data-ttu-id="2c0c3-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]부터 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 스냅샷과 트랜잭션 복제를 사용하여 Oracle 데이터베이스에서 데이터를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-103">Beginning with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows you to publish data from an Oracle database using snapshot and transactional replication.</span></span> <span data-ttu-id="2c0c3-104">자세한 내용은 [Oracle 게시 개요](non-sql/oracle-publishing-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-104">For more information, see [Oracle Publishing Overview](non-sql/oracle-publishing-overview.md).</span></span>  
  
 <span data-ttu-id="2c0c3-105">Oracle 게시자는 원격 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 배포자를 사용해야 합니다. 이 마법사는 필요한 Oracle 네트워킹 소프트웨어를 설치 및 테스트한 후 해당 서버에서 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-105">The Oracle Publisher must use a remote [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor; this wizard must be run on that server after the necessary Oracle networking software has been installed and tested.</span></span> <span data-ttu-id="2c0c3-106">자세한 내용은 [Oracle 게시자 구성](non-sql/configure-an-oracle-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-106">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2c0c3-107">다른 관리자가 Oracle 데이터베이스를 게시자로 구성한 경우 **다음** 을 클릭하면 Oracle 데이터베이스 연결 시 사용되는 복제 로그인 암호를 입력하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-107">If another administrator configured the Oracle database as a Publisher, after clicking **Next** you will be prompted to enter the password for the replication login used to connect to the Oracle database.</span></span> <span data-ttu-id="2c0c3-108">암호를 입력하면[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 Oracle 데이터베이스에 연결된 서버 연결과 사용자 로그인 간 매핑을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will then create a mapping between your login and the linked server connection to the Oracle database.</span></span> <span data-ttu-id="2c0c3-109">이후에 Oracle 데이터베이스에 연결할 때는 암호를 입력할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-109">You will not be required to enter a password for subsequent connections to the Oracle database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2c0c3-110">옵션</span><span class="sxs-lookup"><span data-stu-id="2c0c3-110">Options</span></span>  
 <span data-ttu-id="2c0c3-111">**Oracle 게시자**</span><span class="sxs-lookup"><span data-stu-id="2c0c3-111">**Oracle Publishers**</span></span>  
 <span data-ttu-id="2c0c3-112">목록에서 Oracle 게시자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-112">Select an Oracle Publisher from the list.</span></span> <span data-ttu-id="2c0c3-113">이 목록에는 마법사가 실행 중인 서버를 배포자로 사용하도록 이전에 구성된 Oracle 게시자가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-113">This list contains Oracle Publishers that have previously been configured to use the server against which the wizard is running as their Distributor.</span></span> <span data-ttu-id="2c0c3-114">목록이 비어 있거나 사용할 Oracle 게시자가 목록에 없으면 **Oracle 게시자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-114">If the list is empty, or the Oracle Publisher you want to use is not in the list, click **Add Oracle Publisher**.</span></span>  
  
 <span data-ttu-id="2c0c3-115">**Oracle 게시자 추가**</span><span class="sxs-lookup"><span data-stu-id="2c0c3-115">**Add Oracle Publisher**</span></span>  
 <span data-ttu-id="2c0c3-116">**배포자 속성** 대화 상자를 시작하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-116">Click to launch the **Distributor Properties** dialog box.</span></span> <span data-ttu-id="2c0c3-117">이 대화 상자에서 **추가**를 클릭한 다음 **Oracle 게시자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-117">In this dialog box, click **Add**, and then click **Add Oracle Publisher**.</span></span> <span data-ttu-id="2c0c3-118">**서버에 연결** 대화 상자에서 Oracle 서버 이름과 복제 관리 사용자 스키마의 로그인 및 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-118">In the **Connect to Server** dialog box, specify the Oracle server name, and the login and password for the replication administrative user schema.</span></span> <span data-ttu-id="2c0c3-119">자세한 내용은 [서버에 연결&#40;Oracle&#41;, 로그인](connect-to-server-oracle-login.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-119">For more information, see [Connect to Server &#40;Oracle&#41;, Login](connect-to-server-oracle-login.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2c0c3-120">마법사가 실행 중인 서버가 배포자로 구성되어 있지 않으면 지금 배포자로 구성하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0c3-120">If the server against which the wizard is running has not yet been configured as a Distributor, you are prompted to configure it now.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0c3-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c0c3-121">See Also</span></span>  
 [<span data-ttu-id="2c0c3-122">Oracle 데이터베이스에서 게시 만들기</span><span class="sxs-lookup"><span data-stu-id="2c0c3-122">Create a Publication from an Oracle Database</span></span>](publish/create-a-publication-from-an-oracle-database.md)   

  
  
