---
title: Oracle 테이블스페이스 관리 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a3624aed38a7a5bf75e0c0807aa8d3657156264f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733924"
---
# <a name="manage-oracle-tablespaces"></a><span data-ttu-id="bbe0f-102">Oracle 테이블스페이스 관리</span><span class="sxs-lookup"><span data-stu-id="bbe0f-102">Manage Oracle Tablespaces</span></span>
  <span data-ttu-id="bbe0f-103">테이블스페이스는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 파일 그룹과 개념이 거의 동일한 데이터베이스 스토리지 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-103">A tablespace is a unit of database storage that is roughly equivalent to a file group in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="bbe0f-104">테이블스페이스를 사용하면 개별 그룹 내에서 데이터베이스 개체를 스토리지하고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-104">Tablespaces allow storage and management of database objects within individual groups.</span></span> <span data-ttu-id="bbe0f-105">자세한 내용은 Oracle 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-105">For more information, see the Oracle documentation.</span></span>  
  
 <span data-ttu-id="bbe0f-106">테이블을 Oracle 게시의 일부로 구성하는 경우 복제 로깅 정보를 저장할 때 기존 Oracle 테이블스페이스를 사용하도록 선택적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-106">When you configure a table as part of an Oracle publication, you can optionally specify an existing Oracle tablespace to be used when storing replication logging information.</span></span> <span data-ttu-id="bbe0f-107">지정하지 않으면 복제 개체에 대한 테이블스페이스가 게시자를 구성할 때 구성된 복제 관리 사용자 스키마와 연결된 기본 테이블스페이스가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-107">If unspecified, the tablespace for the replication objects is the default tablespace associated with the replication administrative user schema that was configured when configuring the Publisher.</span></span>  
  
 <span data-ttu-id="bbe0f-108">**아티클 로깅 테이블에 대해 테이블스페이스를 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="bbe0f-108">**To specify a tablespace for an article logging table**:</span></span>  
  
-   <span data-ttu-id="bbe0f-109">**아티클 속성** 대화 상자에서 테이블스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-109">Specify a tablespace in the **Article Properties** dialog box.</span></span> <span data-ttu-id="bbe0f-110">이 대화 상자에 액세스하는 방법은 [게시 속성 보기 및 수정](../publish/view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-110">For more information about accessing this dialog box, see [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md).</span></span>  
  
-   <span data-ttu-id="bbe0f-111">[sp_changearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-111">Use [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span> <span data-ttu-id="bbe0f-112">**sp_changearticle**을 사용하려면 다음을 지정하십시오.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-112">To use **sp_changearticle**, specify the following:</span></span>  
  
    -   <span data-ttu-id="bbe0f-113">매개 변수에 대 한 Oracle 게시자의 이름 **@publisher** 입니다.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-113">The name of the Oracle Publisher for the parameter **@publisher**.</span></span>  
  
    -   <span data-ttu-id="bbe0f-114">매개 변수에 대 한 Oracle 게시의 이름 **@publication** 입니다.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-114">The name of the Oracle publication for the parameter **@publication**.</span></span>  
  
    -   <span data-ttu-id="bbe0f-115">매개 변수에 대 한 아티클의 이름 **@article** 입니다.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-115">The name of the article for the parameter **@article**.</span></span>  
  
    -   <span data-ttu-id="bbe0f-116">매개 변수에 대 한 ' 테이블 스페이스 ' 값입니다 **@property** .</span><span class="sxs-lookup"><span data-stu-id="bbe0f-116">A value of 'tablespace' for the parameter **@property**.</span></span>  
  
    -   <span data-ttu-id="bbe0f-117">매개 변수에 대 한 테이블 스페이스의 이름 **@value** 입니다.</span><span class="sxs-lookup"><span data-stu-id="bbe0f-117">The name of the tablespace for the parameter **@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe0f-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bbe0f-118">See Also</span></span>  
 <span data-ttu-id="bbe0f-119">[Oracle 게시자 구성](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="bbe0f-119">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="bbe0f-120">Oracle 게시자에 생성되는 개체</span><span class="sxs-lookup"><span data-stu-id="bbe0f-120">Objects Created on the Oracle Publisher</span></span>](objects-created-on-the-oracle-publisher.md)  
  
  
