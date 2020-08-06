---
title: 배포자에서 원격 게시자 설정(SQL Server Management Studio) | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- remote Distributors [SQL Server replication]
- Publishers [SQL Server replication]
ms.assetid: 6f8e2831-5c45-4e39-8e51-d37e2813cf3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 06c85924731b79e8b3c79cfbcc354b5bedf69b62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646903"
---
# <a name="enable-a-remote-publisher-at-a-distributor-sql-server-management-studio"></a><span data-ttu-id="6218d-102">배포자에서 원격 게시자 설정(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6218d-102">Enable a Remote Publisher at a Distributor (SQL Server Management Studio)</span></span>
  <span data-ttu-id="6218d-103">**게시자** 페이지에서 원격 배포자를 사용하려면 게시자를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-103">Enable a Publisher to use a remote Distributor on the **Publishers** page.</span></span> <span data-ttu-id="6218d-104">이 페이지는 배포 구성 마법사 및 **배포자 속성 - \<Distributor>** 대화 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-104">This page is available in the Configure Distribution Wizard and the **Distributor Properties - \<Distributor>** dialog box.</span></span> <span data-ttu-id="6218d-105">마법사 사용 방법 및 대화 상자에 액세스하는 방법은 [게시 및 배포 구성](configure-publishing-and-distribution.md) 및 [배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6218d-105">For more information about using the wizard and accessing the dialog box, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md) and [View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md).</span></span>  
  
### <a name="to-enable-a-publisher-in-the-configure-distribution-wizard"></a><span data-ttu-id="6218d-106">배포 구성 마법사에서 게시자를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="6218d-106">To enable a Publisher in the Configure Distribution Wizard</span></span>  
  
1.  <span data-ttu-id="6218d-107">배포 구성 마법사의 **게시자** 페이지에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-107">On the **Publishers** page of the Configure Distribution Wizard, click **Add**.</span></span>  
  
2.  <span data-ttu-id="6218d-108">**SQL Server 게시자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-108">Click **Add SQL Server Publisher**.</span></span> <span data-ttu-id="6218d-109">배포자를 사용하도록 Oracle 게시자를 설정하는 방법은 [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6218d-109">For information about enabling an Oracle Publisher to use a Distributor, see [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
3.  <span data-ttu-id="6218d-110">**서버에 연결** 대화 상자에서 원격 배포자를 사용할 게시자에 대한 연결 정보를 지정한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-110">In the **Connect to Server** dialog box, specify connection information for the Publisher that will use the remote Distributor, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="6218d-111">**배포자 암호** 페이지에서 **암호** 및 **암호 확인** 입력란에 관리 태스크를 수행하기 위해 게시자에서 배포자로 연결할 때 복제에서 사용하는 **distributor_admin** 계정에 대한 강력한 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-111">On the **Distributor Password** page, in the **Password** and **Confirm password** text boxes, specify a strong password for the **distributor_admin** account, which replication uses to connect from the Publisher to the Distributor to perform administrative tasks.</span></span>  
  
5.  <span data-ttu-id="6218d-112">게시자에 대한 설정을 보고 수정하려면 속성 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-112">To view and modify settings for a Publisher, click the properties button (**...**).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-enable-a-publisher-in-the-distributor-properties-dialog-box"></a><span data-ttu-id="6218d-113">배포자 속성 대화 상자에서 게시자를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="6218d-113">To enable a Publisher in the Distributor Properties dialog box</span></span>  
  
1.  <span data-ttu-id="6218d-114">**배포자 속성 - \<Distributor>** 대화 상자의 **게시자** 페이지에서 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-114">On the **Publishers** page of the **Distributor Properties - \<Distributor>** dialog box, click **Add**.</span></span>  
  
2.  <span data-ttu-id="6218d-115">**SQL Server 게시자 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-115">Click **Add SQL Server Publisher**.</span></span> <span data-ttu-id="6218d-116">배포자를 사용하도록 Oracle 게시자를 설정하는 방법은 [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6218d-116">For information about enabling an Oracle Publisher to use a Distributor, see [Create a Publication from an Oracle Database](publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
3.  <span data-ttu-id="6218d-117">**서버에 연결** 대화 상자에서 원격 배포자를 사용할 게시자에 대한 연결 정보를 지정한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-117">In the **Connect to Server** dialog box, specify connection information for the Publisher that will use the remote Distributor, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="6218d-118">**게시자** 페이지에서 **암호** 및 **암호 확인** 입력란에 관리 태스크를 수행하기 위해 게시자에서 배포자로 연결할 때 복제에서 사용하는 **distributor_admin** 계정에 대한 강력한 암호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-118">On the **Publishers** page, in the **Password** and **Confirm password** text boxes, specify a strong password for the **distributor_admin** account, which replication uses to connect from the Publisher to the Distributor to perform administrative tasks.</span></span>  
  
5.  <span data-ttu-id="6218d-119">게시자에 대한 설정을 보고 수정하려면 속성 단추( **...** )를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6218d-119">To view and modify settings for a Publisher, click the properties button (**...**).</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6218d-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6218d-120">See Also</span></span>  
 <span data-ttu-id="6218d-121">[게시 및 배포 구성](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="6218d-121">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="6218d-122">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="6218d-122">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="6218d-123">배포자 보안 설정</span><span class="sxs-lookup"><span data-stu-id="6218d-123">Secure the Distributor</span></span>](security/secure-the-distributor.md)  
  
  
