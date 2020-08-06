---
title: 트랜잭션 게시에서 저장 프로시저 실행 게시 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44310d45a7049701a6aecfa73301b15b0021ac6f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647598"
---
# <a name="publish-the-execution-of-a-stored-procedure-in-a-transactional-publication-sql-server-management-studio"></a><span data-ttu-id="09b73-102">저장 프로시저 실행을 트랜잭션 게시로 게시(SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="09b73-102">Publish the Execution of a Stored Procedure in a Transactional Publication (SQL Server Management Studio)</span></span>
  <span data-ttu-id="09b73-103">**아티클 속성 - \<Article>** 대화 상자에서 해당 정의만이 아닌 저장 프로시저 실행을 게시하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="09b73-103">Specify that the execution of a stored procedure (rather than just its definition) should be published in the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="09b73-104">이 대화 상자는 새 게시 마법사 및 **게시 속성 - \<Publication>** 대화 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="09b73-104">This dialog box is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="09b73-105">마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](create-a-publication.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="09b73-105">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
 <span data-ttu-id="09b73-106">프로시저 정의(CREATE PROCEDURE 문)는 구독이 초기화될 때 구독자로 복제되고 게시자에서 프로시저가 실행되면 복제가 구독자에서 해당하는 프로시저를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="09b73-106">The definition of the procedure (the CREATE PROCEDURE statement) is replicated to the Subscriber when the subscription is initialized; when the procedure is executed at the Publisher, replication executes the corresponding procedure at the Subscriber.</span></span>  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a><span data-ttu-id="09b73-107">저장 프로시저의 실행을 게시하려면</span><span class="sxs-lookup"><span data-stu-id="09b73-107">To publish the execution of a stored procedure</span></span>  
  
1.  <span data-ttu-id="09b73-108">새 게시 마법사의 **아티클** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자에서 저장 프로시저를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="09b73-108">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a stored procedure.</span></span>  
  
2.  <span data-ttu-id="09b73-109">**아티클 속성**을 클릭한 다음 **선택한 저장 프로시저 아티클 속성 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="09b73-109">Click **Article Properties**, and then click **Set Properties of Highlighted Stored Procedure**.</span></span>  
  
3.  <span data-ttu-id="09b73-110">**아티클 속성 - \<Article>** 대화 상자의 **복제** 옵션에 다음 값 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="09b73-110">In the **Article Properties - \<Article>** dialog box, specify one of the following values for the **Replicate** option:</span></span>  
  
    -   <span data-ttu-id="09b73-111">**저장 프로시저 실행**</span><span class="sxs-lookup"><span data-stu-id="09b73-111">**Execution of the stored procedure**</span></span>  
  
    -   <span data-ttu-id="09b73-112">**SP의 직렬화된 트랜잭션에서 실행**</span><span class="sxs-lookup"><span data-stu-id="09b73-112">**Execution in a serialized transaction of the SP**</span></span>  
  
         <span data-ttu-id="09b73-113">이 옵션은 프로시저가 직렬화할 수 있는 트랜잭션의 컨텍스트 내에서 실행될 때만 프로시저 실행을 복제하기 때문에 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="09b73-113">This is the recommended option, because it replicates the procedure execution only if the procedure is executed within the context of a serializable transaction.</span></span> <span data-ttu-id="09b73-114">저장 프로시저가 직렬화할 수 있는 트랜잭션 외부에서 실행되면 게시된 테이블의 데이터 변경 내용이 일련의 DML(데이터 조작 언어) 문으로 복제됩니다.</span><span class="sxs-lookup"><span data-stu-id="09b73-114">If the stored procedure is executed outside of a serializable transaction, changes to data in published tables are replicated as a series of data manipulation language (DML) statements.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="09b73-115">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="09b73-115">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b73-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="09b73-116">See Also</span></span>  
 [<span data-ttu-id="09b73-117">트랜잭션 복제에서 저장 프로시저 실행 게시</span><span class="sxs-lookup"><span data-stu-id="09b73-117">Publishing Stored Procedure Execution in Transactional Replication</span></span>](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
