---
title: 서버에 연결(Oracle), 로그인 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23f5b515fcb1e80416d860e2ff3a2e6be5431819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646369"
---
# <a name="connect-to-server-oracle-login"></a><span data-ttu-id="e258a-102">서버에 연결(Oracle), 로그인</span><span class="sxs-lookup"><span data-stu-id="e258a-102">Connect to Server (Oracle), Login</span></span>
  <span data-ttu-id="e258a-103">**서버에 연결** 대화 상자의 **로그인** 탭을 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 배포자에서 Oracle 게시자로 연결을 설정하는 계정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e258a-103">Use the **Login** tab of the **Connect to Server** dialog box to specify the account under which connections are made from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor to the Oracle Publisher.</span></span> <span data-ttu-id="e258a-104">게시자를 구성하는 중에 복제 관리 사용자 스키마에 대해 지정한 계정과 동일한 계정을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e258a-104">You must use the same account as the one specified for the replication administrative user schema during configuration of the Publisher.</span></span> <span data-ttu-id="e258a-105">자세한 내용은 [Oracle 게시자 구성](non-sql/configure-an-oracle-publisher.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e258a-105">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="e258a-106">옵션</span><span class="sxs-lookup"><span data-stu-id="e258a-106">Options</span></span>  
 <span data-ttu-id="e258a-107">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="e258a-107">**Server instance**</span></span>  
 <span data-ttu-id="e258a-108">배포자에 설치된 Oracle 클라이언트 소프트웨어를 구성하는 중에 지정한 Oracle 게시자의 TNS(Transparent Network Substrate) 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e258a-108">The Transparent Network Substrate (TNS) name of the Oracle Publisher, which is specified during configuration of the Oracle client software installed on the Distributor.</span></span>  
  
 <span data-ttu-id="e258a-109">**인증**</span><span class="sxs-lookup"><span data-stu-id="e258a-109">**Authentication**</span></span>  
 <span data-ttu-id="e258a-110">**Oracle 표준 인증** (권장) 또는 **Windows 인증**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e258a-110">Select **Oracle Standard Authentication** (recommended) or **Windows Authentication**.</span></span> <span data-ttu-id="e258a-111">**Windows 인증**을 선택하는 경우 다음 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e258a-111">If you select **Windows Authentication**:</span></span>  
  
-   <span data-ttu-id="e258a-112">Windows 자격 증명을 사용하는 연결을 허용하도록 Oracle 서버를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e258a-112">The Oracle server must be configured to allow connections using Windows credentials.</span></span> <span data-ttu-id="e258a-113">자세한 내용은 Oracle 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="e258a-113">For more information, see the Oracle documentation.</span></span>  
  
-   <span data-ttu-id="e258a-114">현재 복제 관리 사용자 스키마에 대해 지정한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정으로 로그인되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e258a-114">You must be currently logged in with the same [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account you specified for the replication administrative user schema.</span></span>  
  
 <span data-ttu-id="e258a-115">**로그인** 및 **암호**</span><span class="sxs-lookup"><span data-stu-id="e258a-115">**Login** and **Password**</span></span>  
 <span data-ttu-id="e258a-116">**인증** 옵션을 **Oracle 표준 인증** 으로 선택한 경우 사용할 로그인 및 암호를 지정합니다. 로그인 및 암호는 복제 관리 사용자 스키마에 대해 지정한 것과 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e258a-116">If you selected **Oracle Standard Authentication** for the **Authentication** option, specify the login and password to use, which must be the same as those specified for the replication administrative user schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e258a-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e258a-117">See Also</span></span>  
 [<span data-ttu-id="e258a-118">Oracle 게시를 위한 용어 설명</span><span class="sxs-lookup"><span data-stu-id="e258a-118">Glossary of Terms for Oracle Publishing</span></span>](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
