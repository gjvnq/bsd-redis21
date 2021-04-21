
  * Separar filestreams de filenodes.
  * Aplicar permissões tanto a streams quanto nodes.
  * Usar RediSQL?
  * Filestreams podem ser mutáveis (UUID) ou imutáveis (hash).
  * Filenodes podem apontar para streams (hardlink) ou nodes (softlink)
  * Permissões de filenode:
    * Delete
    * Add child
    * Relink (mudar filestream/filenode apontado pelo node)
  * Permissões sobre metadados (dependem do filenode/filestream e do nome da chave):
    * Add (meio tipo append porque não pode editar depois automaticamente)
    * Edit
    * Delete
  * Permissões sobre filestreams:
    * Add (tipo append porque não pode editar)
    * Read
    * Write
    * Append (to the end of an existing file)
    * Delete
    * RLock
    * WLock
  * Locks tem limite de tempo automático
  * Admin pode dar, automaticemente, Edit/Write para quem adicionou o stream, node ou mentry (metadata entry).
