---
title: 자격 증명(데이터베이스 엔진) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- principals [SQL Server], credentials
- schemas [SQL Server], credentials
- permissions [SQL Server], credentials
- groups [SQL Server], credentials
- ALTER ANY CREDENTIAL permission
- security [SQL Server], credentials
- authentication [SQL Server], credentials
- users [SQL Server], credentials
- credentials [SQL Server], about credentials
- credentials [SQL Server]
ms.assetid: c8df6022-e0b4-46b8-9670-3f86938d3177
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: faa2b5be7cf6918b5d5232763a96ed4dbbc89e51
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653774"
---
# <a name="credentials-database-engine"></a><span data-ttu-id="5ed43-102">자격 증명(데이터베이스 엔진)</span><span class="sxs-lookup"><span data-stu-id="5ed43-102">Credentials (Database Engine)</span></span>
  <span data-ttu-id="5ed43-103">자격 증명은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]외부의 리소스에 연결하는 데 필요한 인증 정보(자격 증명)가 포함된 레코드입니다.</span><span class="sxs-lookup"><span data-stu-id="5ed43-103">A credential is a record that contains the authentication information (credentials) required to connect to a resource outside [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5ed43-104">이 정보는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 내부적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ed43-104">This information is used internally by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5ed43-105">대부분의 자격 증명에는 Windows 사용자 이름 및 암호가 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ed43-105">Most credentials contain a Windows user name and password.</span></span>  
  
 <span data-ttu-id="5ed43-106">자격 증명에 저장된 정보를 사용하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인증을 통해 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에 연결된 사용자가 서버 인스턴스 외부의 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ed43-106">The information stored in a credential enables a user who has connected to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] by way of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Authentication to access resources outside the server instance.</span></span> <span data-ttu-id="5ed43-107">외부 리소스가 Windows인 경우 사용자는 자격 증명에서 지정한 Windows 사용자로 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ed43-107">When the external resource is Windows, the user is authenticated as the Windows user specified in the credential.</span></span> <span data-ttu-id="5ed43-108">하나의 자격 증명을 여러 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인에 매핑할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="5ed43-108">A single credential can be mapped to multiple [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] logins.</span></span> <span data-ttu-id="5ed43-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로그인은 하나의 자격 증명에만 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ed43-109">However, a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] login can be mapped to only one credential.</span></span>  
  
 <span data-ttu-id="5ed43-110">시스템 자격 증명은 자동으로 생성되며 특정 엔드포인트와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ed43-110">System credentials are created automatically and are associated with specific endpoints.</span></span> <span data-ttu-id="5ed43-111">시스템 자격 증명의 이름은 2개의 해시 기호(##)로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ed43-111">Names for system credentials start with two hash signs (##).</span></span>  
  
 <span data-ttu-id="5ed43-112">자격 증명에 대 한 자세한 내용은 [sys. 자격 증명](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) 카탈로그 뷰를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ed43-112">For more information about credentials, see the [sys.credentials](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) catalog view.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="5ed43-113">관련 내용</span><span class="sxs-lookup"><span data-stu-id="5ed43-113">Related Content</span></span>  
 <span data-ttu-id="5ed43-114">[자격](../authentication-access/create-a-credential.md) 증명 만들기 [자격 증명 만들기 transact-sql&#41;&#40;](/sql/t-sql/statements/create-credential-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="5ed43-114">[Create a Credential](../authentication-access/create-a-credential.md) [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)</span></span>  
  
 [<span data-ttu-id="5ed43-115">SQL Server 보안 설정</span><span class="sxs-lookup"><span data-stu-id="5ed43-115">Securing SQL Server</span></span>](../securing-sql-server.md)  
  
  
